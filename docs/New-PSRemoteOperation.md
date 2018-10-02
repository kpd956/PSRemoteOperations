---
external help file: PSRemoteOperations-help.xml
Module Name: PSRemoteOperations
online version:
schema: 2.0.0
---

# New-PSRemoteOperation

## SYNOPSIS

Create a new remote operation file.

## SYNTAX

### scriptblock (Default)

```yaml
New-PSRemoteOperation [-Computername] <String> -Scriptblock <ScriptBlock> [-ArgumentList <Object[]>]
 [-Initialization <ScriptBlock>] [-Path <String>] [-Passthru] [<CommonParameters>]
```

### filepath

```yaml
New-PSRemoteOperation [-Computername] <String> -ScriptPath <String> [-ArgumentList <Object[]>]
 [-Initialization <ScriptBlock>] [-Path <String>] [-Passthru] [<CommonParameters>]
```

## DESCRIPTION

Use this command to create a new remote operation file. You should specify a path that the remote computer will monitor. It is recommended that you set a global variable called PSRemoteOpPath with this value. If you don't define this variable and don't specify a Path value, the command will fail.

## EXAMPLES

### Example 1

```powershell
PS C:\> New-PSRemoteOperation -computername Foo -scriptblock {Restart-Service spooler -force}
```

This will create a remote operating psd1 file using the value of $PSRemoteOpPath for computer Foo

### Example 2

```powershell
PS C:\> New-PSRemoteOperation -computername Foo -scriptblock {Restart-Service spooler -force} -path \\DSFile\Watch -passthru


    Directory: \\DSFile\Watch


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/2/2018   3:46 PM            342 foo_ed5ea30c-974a-4790-94fb-da91b6f85ef6.psd1
```

Repeat the previous example but create the file in a UNC path and pass the file object to the pipeline.

## PARAMETERS

### -ArgumentList

An array of objects to pass as arguments. Values are positional to your script or scriptblock.

```yaml
Type: Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Computername

Enter the name of the computer where this command will execute.

```yaml
Type: String
Parameter Sets: (All)
Aliases: CN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Initialization

A script block of commands to run prior to executing your script or scriptblock.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Passthru

Write the operation object to the pipeline.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

The folder where the remote operation file will be created. The command will default to the value in the global variable PSRemoteOpPath.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $PSRemoteOpPath
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPath

Enter the path to the PowerShell script to execute. This is relative to the remote computer.

```yaml
Type: String
Parameter Sets: filepath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scriptblock

Enter a scriptblock to execute.

```yaml
Type: ScriptBlock
Parameter Sets: scriptblock
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### None

### System.IO.FileInfo

## NOTES

    Learn more about PowerShell: http://jdhitsolutions.com/blog/essential-powershell-resources/

## RELATED LINKS

[about_PSRemoteOperations]()

[Register-PSRemoteOperationWatcher]()