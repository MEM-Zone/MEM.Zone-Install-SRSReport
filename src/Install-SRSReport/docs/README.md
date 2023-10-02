[![Release version][release-version-badge]][release-version]
[![Release date][release-date-badge]][release-date]
[![Issues count][issues-badge]][issues]
[![Comits since release][commits-since-badge]][commits-since]
[![Chat on discord][discord-badge]][discord]
[![Follow on twitter][twitter-badge]][twitter]

# Install-SRSReport

This is a solution installing SRS Reports using PowerShell.

## Latest release

See [releases](https://MEMZ.one/Install-SRSReport-RELEASES).

## Changelog

See [changelog](https://MEMZ.one/Install-SRSReport-CHANGELOG).

## Prerequisites

### Software

* Microsoft SQL Server Reporting Services (SSRS) 2017 or above.
* [ReportingServiceTools cmdlet](https://github.com/microsoft/ReportingServicesTools)

> Notes
> If the ReportingServiceTools is not present the user will be asked to allow installation.

## Functions

### Get-RINode

Gets a report item node information.

### Set-RINodeValue

Updates the shared DataSource of a report or multiple reports on a report server.

### Install-RIReport

Uploads a report or reports in a folder on disk to a report server.

### Set-RIDataSourceReference

Updates the shared DataSource of a report or multiple reports on a report server.

### Add-RISQLExtension

Adds sql extension(s) from a folder on disk to specified SQL database.

## Extensions

There are two types of extensions currently supported. You can find two examples in the `Extensions` folder.
Extensions are useful when you need to add user defined functions or give additional rights for your imported reports.

* Permission
* User Defined function

Notes
> The extensions need to be in the same folder and have the `perm` for Permission or `ufn` for user defined function prefix.

## Usage

```PowerShell
## Get syntax help
Get-Help .\Install-SRSReport.ps1

## Typical installation example
#  With extensions
.\Install-SRSReport.ps1 -ReportServerUri 'http://CM-SQL-RS-01A/ReportServer' -ReportFolder '/ConfigMgr_XXX/SRSDashboards' -ServerInstance 'CM-SQL-RS-01A' -Database 'CM_XXX' -Overwrite -Verbose
#  Without extensions (Permissions will still be granted on prerequisite views and tables)
.\Install-SRSReport.ps1 -ReportServerUri 'http://CM-SQL-RS-01A/ReportServer' -ReportFolder '/ConfigMgr_XXX/SRSDashboards' -ServerInstance 'CM-SQL-RS-01A' -Database 'CM_XXX' -ExcludeExtensions -Verbose
#  Extensions only
.\Install-SRSReport.ps1 -ServerInstance 'CM-SQL-RS-01A' -Database 'CM_XXX' -ExtensionsOnly -Overwrite -Verbose
```

>**Notes**
> If you don't use `Windows Authentication` (you should!), you can use the `-UseSQLAuthentication` switch.
> PowerShell script needs to be run as administrator.

## Preview

![](https://github.com/MEM-Zone/Install-SRSReport/blob/master/Install-SRSReport/Preview/Install-SSRSReport.gif)

[release-version-badge]: https://img.shields.io/github/v/release/MEM-Zone/Install-SRSReport
[release-version]: https://github.com/MEM-Zone/Install-SRSReport/releases
[release-date-badge]: https://img.shields.io/github/release-date-pre/MEM-Zone/Install-SRSReport
[release-date]: https://github.com/MEM-Zone/Install-SRSReport/releases
[issues-badge]: https://img.shields.io/github/issues/MEM-Zone/Install-SRSReport
[issues]: https://github.com/MEM-Zone/Install-SRSReport/issues?q=is%3Aopen+is%3Aissue
[commits-since-badge]: https://img.shields.io/github/commits-since/MEM-Zone/Install-SRSReport/v1.1.6
[commits-since]: https://github.com/MEM-Zone/Install-SRSReport/commits/master
[discord-badge]: https://img.shields.io/discord/666618982844989460?logo=disco
[discord]: https://discord.gg/dz2xcDz
[twitter-badge]: https://img.shields.io/twitter/follow/ioanpopovici?style=social&logo=twitter
[twitter]: https://twitter.com/intent/follow?screen_name=ioanpopovici
