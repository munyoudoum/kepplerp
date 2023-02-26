# kepplerp
kepplerp(ublic): to run keppler along with ngrok

<!-- https://raw.githubusercontent.com/munyoudoum/kepplerp/master/kepplerp -->

## Install
### Method 1: Download to /usr/local/bin and make executable

```bash
curl -L https://raw.githubusercontent.com/munyoudoum/kepplerp/master/kepplerp -o /usr/local/bin/kepplerp && chmod +x /usr/local/bin/kepplerp
```

### Method 2: Download and alias to kepplerp

```bash
curl -L https://raw.githubusercontent.com/munyoudoum/kepplerp/master/kepplerp -o ~/kepplerp && chmod +x ~/kepplerp && alias kepplerp="~/kepplerp"
```

## Usage

```bash
kepplerp <arguments>
```

## With authentication

```bash
kepplerp --auth 'user:pass'
```
