
# haveibeenpwned-sha1-query

Check a password securely in the [Pwned Passwords database](https://haveibeenpwned.com/Passwords). Go to the [page](https://sashee.github.io/haveibeenpwned-sha1-query/) and input an SHA-1 to see if it is breached.

## How to check your password

### Generate the SHA-1 securely

* Open a new Incognito window
* Press F12 to open the developer toolbar
* Go to the **Network** tab
* Check the **Offline** checkbox
* Go to the **Console** tab
* Paste this code and press *enter*:

```
async function sha1(message) {
  const msgBuffer = new TextEncoder('utf-8').encode(message);
  const hashBuffer = await crypto.subtle.digest('SHA-1', msgBuffer);
  const hashArray = Array.from(new Uint8Array(hashBuffer));
  const res = hashArray.map(b => ('00' + b.toString(16)).slice(-2)).join('');
  console.log(res);
}
```
* Enter ```sha1("...")```, substituting ```...``` with your password, then press enter
* You'll see a bunch of characters and numbers, similar to this: ```a9993e364706816aba3e25717850c26c9cd0d89d```
* This is the password's SHA-1 hash, copy it
* Close the incognito window

### Check the SHA-1

* Go to [https://sashee.github.io/haveibeenpwned-sha1-query/](https://sashee.github.io/haveibeenpwned-sha1-query/)
* Enter the SHA-1, then click the button
* It will show whether the password is a known breached password
