# 🧪 Custom ANTA Tests – Windows + VSCode Setup Guide

This guide will walk you through cloning the repo, setting up your environment, and running custom ANTA tests using **Visual Studio Code** and **PowerShell** on **Windows**.

---

## 📥 1. Clone the Repository

Open PowerShell or use the integrated terminal in VSCode:

```powershell
git clone https://github.com/natedoot/anta-playground.git
cd anta-playground
```

---

## 🛠️ 2. Install Python Requirements

Make sure you have Python 3.8+ installed and available in your system PATH.

Install the package in editable mode:

```powershell
pip install -e .
```

---

## 📁 3. Set PYTHONPATH for Custom ANTA Tests

ANTA requires your custom test directory to be included in the `PYTHONPATH`.

In PowerShell (within VSCode), run:

```powershell
$env:PYTHONPATH = "$env:PYTHONPATH;$(Get-Location)\custom_anta_tests"
```

> This is required every time you open a new terminal unless made persistent (see below).

---

## ✅ 4. Verify PYTHONPATH

Check that your custom path is present in the Python path:

```powershell
python -c "import sys; print(sys.path)"
```

You should see something like:
```
C:\Users\YourName\Path\To\Repo\custom_anta_tests
```

---

## 🧪 5. Run ANTA with Your Custom Tests

You can now run your custom tests using ANTA:

```powershell
anta nrfu -u <user> -p <pass> --inventory anta_inventory.yml --catalog custom_vlan_catalog.yml
```

---

## 🧰 Recommended VSCode Extensions

- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

---

## 🐍 Troubleshooting

- **PYTHONPATH not working?**
  Make sure you're running `anta` in the same PowerShell session where you set the variable.

- **ANTA not found?**
  Confirm it's installed (`pip show anta`) or try installing it manually:
  ```powershell
  pip install anta
  ```

---

## 🙌 Done!

You're now ready to develop and run custom ANTA tests from a Windows environment using VSCode and PowerShell.
