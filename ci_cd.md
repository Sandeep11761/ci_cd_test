# Create a folder under the drive root
$ mkdir actions-runner; cd actions-runner

# Download the latest runner package

$ Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.323.0/actions-runner-win-x64-2.323.0.zip -OutFile actions-runner-win-x64-2.323.0.zip# Optional: Validate the hash
$ if((Get-FileHash -Path actions-runner-win-x64-2.323.0.zip -Algorithm SHA256).Hash.ToUpper() -ne 'e8ca92e3b1b907cdcc0c94640f4c5b23f377743993a4a5c859cb74f3e6eb33ef'.ToUpper()){ throw 'Computed checksum did not match' }

# Extract the installer
$ Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$PWD/actions-runner-win-x64-2.323.0.zip", "$PWD")

## configuration
# Create the runner and start the configuration experience
$ ./config.cmd --url https://github.com/Sandeep11761/ci_cd_test --token BK6OQZDQNRUVJGJ4SAD5Z2LIEDHJQ
# Run it!
$ ./run.cmd


# This runner will have the following labels: 'self-hosted', 'Windows', 'X64'

# service name: actions.runner.Sandeep11761-ci_cd_test.DESKTOP-G592QSN  Restart-Service "actions.runner.YOUR_RUNNER_NAME"
# Restart-Service " actions.runner.Sandeep11761-ci_cd_test.DESKTOP-G592QSN" 
