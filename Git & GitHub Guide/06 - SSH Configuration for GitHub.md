



# 6. SSH Configuration for GitHub

SSH is a more stable authentication method than HTTPS.

SSH is generally:

- More stable
- Faster
- More convenient
- Better for long-term use


## Step 1: Generate SSH Key

Open Git Bash and type:

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

Next, you’ll be asked for:

**Save location**

Just press Enter (the default setting is fine):

Enter file in which to save the key

👉 Just press Enter

**Passphrase**

You can:
- Just press Enter (no passphrase—simple)
-  set a passphrase (more secure)

👉 Tip for beginners: Just press Enter twice

## Step 2: Show Public Key

Type:

```bash
cat ~/.ssh/id_ed25519.pub
```
It will output a long string:

>ssh-ed25519 AAAAC3... your@email.com


Copy the output.


## Step 3: Add SSH Key to GitHub

Go to:

GitHub → Settings → SSH and GPG keys → New SSH key

Fill in:
- Title: Enter anything (e.g., my laptop)
- Key: Paste the content you just copied

Then click:
>Add SSH key


## Step 4: Test SSH Connection

Open Git Bash and type:

```bash
ssh -T git@github.com
```

If successful, you will see:

```text
Hi USERNAME! You've successfully authenticated.
```

## Step 5: Change Remote URL to SSH

Enter to the project directory

```bash
cd /d/Code/YourRepository
```

Check current remote:

```bash
git remote -v
```

Before the change, you would see:

```text
https://github.com/xxx/xxx.git
```

Change HTTPS to SSH:

```bash
git remote set-url origin git@github.com:xxx/xxx.git
```

Verify SSH Remote

```bash
git remote -v
```

You should now see:

```text
git@github.com:xxx/xxx.git
```

## Note

When you connect to GitHub via SSH for the first time, Git shows a security prompt:

>The authenticity of host 'github.com' can’t be established. Are you sure you want to continue connecting?

This simply means your computer has never connected to GitHub before and is asking whether to trust the server.

It is a normal SSH security warning, not an error.

What you should do

Type:


```bash
yes
```

and press Enter.

What happens next
- Git saves GitHub’s fingerprint locally
- You won’t be asked again in the future
- The SSH connection process continues normally

Is this dangerous?

No.

This is a standard SSH security mechanism to prevent connecting to fake servers.

GitHub’s fingerprint is publicly known and trusted, so it is safe to accept.

When to be careful

Only be cautious if:

- You are not connecting to `github.com`
- The fingerprint does not match the official one

After successful connection

You should see a message like:

```
Hi username! You've successfully authenticated
```

At this point:

- SSH setup is complete
- GitHub connection is secure
- You can use `git push` normally without HTTPS authentication




## Step 6: Push Using SSH

```bash
git push
```

## HTTPS vs SSH

| Method | Authentication | Stability | Recommendation |
|---|---|---|---|
| HTTPS | Password / Token | Less stable | Basic |
| SSH | SSH Key | Very stable | Recommended |

## Final Recommendation

For long-term development:

✅ Use SSH  
✅ Commit regularly  
✅ Learn Git workflows early  
✅ Treat Git as part of programming itself