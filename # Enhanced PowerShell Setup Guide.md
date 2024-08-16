# Enhanced PowerShell Setup Guide

## 1. Update PowerShell

1. Visit the official PowerShell GitHub releases page: https://github.com/PowerShell/PowerShell/releases
2. Download the latest stable version for your system (e.g., "PowerShell-7.x.x-win-x64.msi" for 64-bit Windows)
3. Run the installer and follow the prompts
4. After installation, launch PowerShell 7 from the Start menu

## 2. Update PSReadLine

1. Open PowerShell 7
2. Run the following command:
   ```powershell
   Install-Module PSReadLine -Force -SkipPublisherCheck
   ```

## 3. Configure PowerShell

1. Open your PowerShell profile for editing:
   ```powershell
   notepad $PROFILE
   ```
2. Replace the contents with the following configuration:

   ```powershell
    Import-Module PSReadLine

    # Enable predictive IntelliSense
    Set-PSReadLineOption -PredictionSource History

    # Optional: Change the view style to ListView (for a dropdown-like appearance)
    Set-PSReadLineOption -PredictionViewStyle ListView

    # Optional: Change colors
    Set-PSReadLineOption -Colors @{ InlinePrediction = "$([char]0x1b)[36;7;238m" }

    # Optional: Use Ctrl+Space to accept the current suggestion
    Set-PSReadLineKeyHandler -Chord "Ctrl+Spacebar" -Function AcceptSuggestion
   ```

3. Save the file and close Notepad
4. Reload your profile:
   ```powershell
   . $PROFILE
   ```

## 4. Verify Setup

1. Close and reopen PowerShell 7
2. Check your PowerShell version:
   ```powershell
   $PSVersionTable.PSVersion
   ```
   Ensure it shows version 7 or higher

## 5. Usage Guide

- As you type, you'll see a dropdown list of suggestions based on your command history
- Use arrow keys to navigate the suggestion list
- Press Tab to cycle through completion options
- Use Ctrl+F to accept the inline suggestion
- Up/Down arrows will search through your command history
- Alt+A cycles through command arguments for quick editing

## Troubleshooting

If you encounter any issues:
1. Ensure you're running PowerShell 7 (not Windows PowerShell 5.1)
2. Check if PSReadLine is imported correctly:
   ```powershell
   Get-Module PSReadLine
   ```
3. If PSReadLine isn't loaded, try importing it manually:
   ```powershell
   Import-Module PSReadLine
   ```
4. If problems persist, try removing and reinstalling PSReadLine:
   ```powershell
   Uninstall-Module PSReadLine -AllVersions
   Install-Module PSReadLine -Force
   ```

Remember to restart PowerShell after making changes to see the effects.