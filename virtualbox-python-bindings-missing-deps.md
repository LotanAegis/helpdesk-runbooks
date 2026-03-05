# VirtualBox install: “Missing Dependencies” (Python bindings)

## Summary
During Oracle VirtualBox 7.2.6 install on Windows, installer prompts that Python Core + win32api bindings are required for Python bindings.

## Impact
- VirtualBox can still be installed and used for normal VM usage.
- Only affects automation via VirtualBox’s Python API.

## Environment
- OS: Windows 10/11
- App: Oracle VirtualBox 7.2.6 (amd64)

## Symptoms
- Installer popup: “Missing Dependencies… requires Python Core package and win32api bindings…”

## Cause
Python bindings are optional components and require:
- Python 3 (64-bit) installed
- `pywin32` package (provides win32api)

## Resolution
### Option A (no Python automation needed)
1. Click **No** on the prompt
2. Continue installation
3. Verify VirtualBox launches and can create/start a VM

### Option B (enable Python automation)
1. Install Python 3 (64-bit) and enable PATH + pip
2. Install pywin32:
   - `py -m pip install --upgrade pip`
   - `py -m pip install pywin32`
3. Re-run VirtualBox installer and click **Yes**

## Verification
- `py -c "import win32api; print('pywin32 OK')"`
- VirtualBox opens successfully

## Notes
If only running VMs, skip Python bindings to keep setup minimal.
