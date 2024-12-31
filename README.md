# Kiểm tra hệ thống Exchange

## Retrieve POP and IMAP settings
```bash
Get-PopSettings | fl
Get-ImapSettings | fl
```
## Receive Connector configurations
```bash
Get-ReceiveConnector
Get-ReceiveConnector "EX2019-01\Default EX2019-01" | fl
```
## Send Connector configurations
```bash
Get-SendConnector
Get-SendConnector "SMG" | fl
```

## Mailbox Database status and details
```bash
Get-MailboxDatabaseCopyStatus
Get-MailboxDatabase

Get-MailboxDatabase -Status | Select-Object Name, DatabaseSize, AvailableNewMailboxSpace | Format-Table -AutoSize
Get-MailboxDatabase -Status -IncludePreExchange | Sort Name | Format-Table Name, Server, Mounted
```

## Mailbox statistics
```bash
Get-MailboxStatistics -Identity abc@domain.vn

Get-MailboxStatistics -Server HUB-EXCHANGE01 | Sort-Object TotalItemsize | Export-Csv "C:\MailboxesStatic-hub-exchange01.csv"
Get-MailboxStatistics -Server HUB-EXCHANGE02 | Sort-Object TotalItemsize | Export-Csv "C:\MailboxesStatic-hub-exchange02.csv"
```

## Transport Configuration
```bash
Get-TransportConfig | fl
Get-TransportConfig | Format-List MaxReceiveSize,MaxSendSize,MaxRecipientEnvelopeLimit

Get-ReceiveConnector | Format-Table Name,Max*Size,MaxRecipientsPerMessage;
Get-SendConnector | Format-Table Name,MaxMessageSize;
Get-AdSiteLink | Format-Table Name,MaxMessageSize;
Get-DeliveryAgentConnector | Format-Table Name,MaxMessageSize;
Get-ForeignConnector | Format-Table Name,MaxMessageSize
```

## Exchange Certificates
```bash
Get-ExchangeCertificate
```
## Virtual Directories and Client Access Settings
```bash
Get-OabVirtualDirectory | fl server, Name, *URL*, *auth*
Get-WebServicesVirtualDirectory | fl server, Name, *URL*, *auth*, MRSProxyEnabled
Get-EcpVirtualDirectory | fl server, Name, *URL*, *auth*
Get-OwaVirtualDirectory | fl server, Name, *URL*, *auth*
Get-ActiveSyncVirtualDirectory | fl server, Name, *URL*, *auth*
Get-ClientAccessServer | fl Name, OutlookAnywhereEnabled, AutodiscoverServiceInternalUri
Get-ExchangeCertificate | fl FriendlyName, Subject, CertificateDomains, Services, Issuer, *not*, Status
Get-OutlookAnywhere | fl server, Name, *URL*, *hostname*, *auth*
Get-MapiVirtualDirectory | fl server, Name, *URL*, *auth*
Get-OrganizationConfig | fl *mapi*
Get-ClientAccessArray | fl
Get-OutlookProvider
Get-ExchangeServer | fl name, *admin*, static*
Get-RpcClientAccess -Server EX2019-01 | fl
Get-ClientAccessServer EX2019-01 | fl
Get-OrganizationConfig | fl
```
.\GetExchangeURLs.ps1 -Server "EX2019"



