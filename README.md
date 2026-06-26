# MongoDB Dashboard - Local Domain Setup

## Register `mongodbdashboard.com` in Windows hosts file

Add this entry to `C:\Windows\System32\drivers\etc\hosts`:

```
127.0.0.1   mongodbdashboard.com
```

## Open hosts file in Notepad as Administrator

Run this command in PowerShell or Run dialog (Win + R):

```powershell
Start-Process notepad "C:\Windows\System32\drivers\etc\hosts" -Verb RunAs
```

Or from the Start menu:
1. Search for **Notepad**
2. Right-click → **Run as administrator**
3. Open file: `C:\Windows\System32\drivers\etc\hosts`

## Add the entry

At the bottom of the hosts file, add:

```
127.0.0.1   mongodbdashboard.com
```

Save the file (`Ctrl + S`), then flush DNS:

```powershell
ipconfig /flushdns
```

## Verify

```powershell
curl.exe -I http://mongodbdashboard.com
```

## Kubernetes Namespace

Switch to the mongo namespace permanently:

```powershell
kubectl config set-context --current --namespace=mongo
```

Or view resources in mongo namespace without switching:

```powershell
kubectl get all -n mongo
```
