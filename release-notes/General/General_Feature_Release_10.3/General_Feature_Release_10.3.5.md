---
uid: General_Feature_Release_10.3.5
---

# General Feature Release 10.3.5 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
>
> - For release notes related to DataMiner Cube, see [DataMiner Cube Feature Release 10.3.5](xref:Cube_Feature_Release_10.3.5).
> - For release notes related to the DataMiner web applications, see [DataMiner web apps Feature Release 10.3.5](xref:Web_apps_Feature_Release_10.3.5).
> - For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

## Highlights

## Other features

#### GQI: New 'ThenSort by' query node allows sorting by multiple columns [ID_35807] [ID_35834]

<!-- MR 10.4.0 - FR 10.3.5 -->

To make sorting more intuitive, the new *ThenSort by* node can now be used in combination with the *Sort* node, which has now been renamed to *Sort by*.

Up to now, all sorting had to be configured by means of *Sort* nodes. For example, if you wanted to first sort by column A and then by column B, you had to create a query in the following counter-intuitive way:

1. Data source
1. Sort by B
1. Sort by A

or

1. Query X (i.e. Data Source, sorted by B)
1. Sort by A

From now on, you can create a query in a much more intuitive way. For example, if you want to first sort by column A and then by column B, you can now create a query in the following way:

1. Data source
1. Sort by A
1. Then sort by B

Note that, from now on, every *Sort by* node will nullify any preceding *Sort by* node. For example, in the following query, the *Sort by B* node will be nullified by the *Sort by A* node, meaning that the result set will only be sorted by column A.

1. Data source
1. Sort by B
1. Sort by A

> [!NOTE]
> The behavior of existing queries (using e.g. *Sort by B* followed by *Sort by A*) will not be altered in any way. Their syntax will automatically be adapted when they are migrated to the most recent GQI version.
> For example, an existing query using *Sort by B* followed by *Sort by A* will use *Sort by A* followed by *Then sort by B* after being migrated.

## Changes

### Enhancements

#### SLNetClientTest: New DOM-related features [ID_35550]

<!-- MR 10.4.0 - FR 10.3.5 -->

In the *SLNetClientTest* tool, the following new DOM-related features have been made available:

- Viewing a JSON representation of a selected ModuleSettings configuration.

- Completely remove a DOM Manager from the system.

  > [!NOTE]
  >
  > - When you instruct the *SLNetClientTest* tool to delete a DOM Manager, it will count the number of DOM instances. If the DOM Manager in question contains more than 10,000 DOM instances, an error message will appear, saying that deleting the DOM Manager would take too long.

  > - When you instruct the *SLNetClientTest* tool to delete a DOM Manager, it will not remove the indices from the Elasticsearch database. These indices have to be deleted manually. If you do not delete them manually, we recommend to not re-use the module ID as this could cause configuration conflicts.

> [!CAUTION]
> Always be extremely careful when using this tool, as it can have far-reaching consequences on the functionality of your DataMiner System.

#### Security enhancements [ID_35668]

<!-- MR 10.4.0 - FR 10.3.5 -->

A number of security enhancements have been made.

#### SLAnalytics: A message will be added to the SLAnalytics.txt log file when no Cassandra database is present [ID_35748]

<!-- MR 10.4.0 - FR 10.3.5 -->

Up to now, SLAnalytics would stop working without giving any notice whatsoever when it was started on a system without a Cassandra database.

From now on, when no Cassandra database is present, SLAnalytics will be stopped gracefully and a message will be added to the *SLAnalytics.txt* log file.

#### Alarms generated when a database goes in offload mode will now have severity 'Notice' instead of 'Critical' [ID_35749]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When a database went in offload mode, up to now, an alarm with severity *Critical* was generated. From now on, an alarm of severity *Notice* will be generated instead.

#### SLNetClientTest: More user-friendly pop-up window will now appear when connecting to a DMA that uses external authentication via SAML [ID_35755]

<!-- MR 10.4.0 - FR 10.3.5 -->

When, in the SLNetClientTest tool, you connected to a DataMiner Agent that used external authentication via SAML, up to now, a pop-up window showing the authentication URL would prompt you to enter the SAML response string. From now on, a pop-up window similar to the one used in Cube will appear instead.

> [!CAUTION]
> Always be extremely careful when using this tool, as it can have far-reaching consequences on the functionality of your DataMiner System.

#### GQI: Raw datetime values retrieved from Elasticsearch will now be converted to UTC [ID_35784]

<!-- MR 10.4.0 - FR 10.3.5 -->
<!-- Not added to MR 10.4.0 -->

Up to now, after each step in a GQI query, raw datetime values were always converted to the time zone that was specified in the query options. From now on, raw datetime values retrieved from Elasticsearch will be converted to UTC instead. The time zone specified in the query options will now only be used when converting a raw datetime value to a display value.

#### SLAnalytics will no longer disregard first-time alarm template assignments [ID_35794]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

Up to now, SLAnalytics only took into account changes to alarm templates that were already assigned to elements and disregarded first-time alarm template assignments.

From now on, SLAnalytics will also take into account first-time alarm template assignments.

#### Business Intelligence: Enhancements with regard to the retrieval of data from logger tables and to general error handling [ID_35820]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

A number of enhancements have been made to the Business Intelligence module, especially with regard to the retrieval of data from logger tables and to general error handling.

#### DataMiner Storage Module: Installer enhancements [ID_35842]

<!-- MR 10.4.0 - FR 10.3.5 -->
<!-- Not added to MR 10.4.0 -->

A number of enhancements have been made to the DataMiner Storage Module installer.

#### SLAnalytics: Enhanced performance [ID_35871]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

Overall performance of SLAnalytics has increased because of a number of enhancements made to its caching mechanism.

#### SLAnalytics - Behavioral anomaly detection: Events associated with a DVE child element will no longer be linked to the DVE parent element [ID_35901]

<!-- MR 10.4.0 - FR 10.3.5 -->

Up to now, when an event associated with a DVE child element was generated, internally, that event would be linked to the DVE parent element. From now on, it will be linked to the child element instead.

#### GQI data sources that require an Elasticsearch database will now use GetInfoMessage(InfoType.Database) to check whether Elasticsearch is available [ID_35907]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

Up to now, GQI data sources that require an Elasticsearch database used the `DatabaseStateRequest<ElasticsearchState>` message to check whether Elasticsearch was available. From now on, they will use the `GetInfoMessage(InfoType.Database)` message instead.

### Fixes

#### SLLogCollector: Problem when collecting multiple memory dumps with the 'Now and when memory increases with X Mb' option [ID_35617]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When the *SLLogCollector* tool had to collect memory dumps of multiple processes with the *Now and when memory increases with X Mb* option, it would incorrectly only collect the memory dump of the first process that reached the specified Mb limit.

From now on, it will collect at least the "now" dump for each of the selected processes.

#### NATS would incorrectly be re-installed when a WMI query error occurred while the NATS installer was being run at DMA startup [ID_35647]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When the NATS installer was being run at DMA startup, in some cases, due to an issue with a WMI query, NATS could incorrectly be re-installed, even though NATS and NAS were already running.

From now on, the execution of the NATS installer at DMA startup will be skipped when NATS is already running. Also, if an error occurs when running a WMI query during the execution of the NATS installer, a message saying that the re-installation has failed will be added to the *SLUMSEndpointManager.txt* log file.

> [!NOTE]
> When an error occurs while running a WMI query, and no NATS/NAS service is running, NATS will not be installed automatically. A manual installation of NATS will be needed.

#### DateTime instances would not get serialized correctly when an SLNet connection supported protocol buffer serialization [ID_35777]

<!-- MR 10.4.0 - FR 10.3.5 -->

When an SLNet connection supported protocol buffer serialization, DateTime instances would not get serialized correctly.

#### SLProtocol would interpret signed numbers incorrectly [ID_35796]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

SLProtocol would interpret signed numbers incorrectly, causing parameters to display incorrect values.

#### Problem with SLNet when serializing a ModelHost error [ID_35802]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

An SLNet error could occur when serializing a ModelHost error.

> [!IMPORTANT]
> BREAKING CHANGE: To fix this issue, the `Exception` field had to be removed from the `ManagerStoreError` class.

#### SLAnalytics: Flatline events on child DVE elements would incorrectly be cleared automatically [ID_35818]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

Events generated after detecting change points of type "flatline" in trend data of child DVE elements would incorrectly be cleared automatically.

#### SLAnalytics - Behavioral anomaly detection: Every parameter included in an alarm template would incorrectly be considered a monitored parameter [ID_35832]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

SLAnalytics would incorrectly consider every parameter included in an alarm template to be a monitored parameter, even it is was not being monitored.

#### DataMiner Maps: Markers could disappear when a layer was enabled or disabled [ID_35838]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

In some cases, markers could disappear when a layer was enabled or disabled.

#### SLAnalytics could keep on waiting indefinitely for large delete operations to finish [ID_35848]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

In some cases, SLAnalytics could keep on waiting indefinitely for large delete operations to finish.

#### Business Intelligence: At SLA startup, the active alarms would no longer be in sync with the actual alarms affecting the SLA [ID_35862]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

At SLA startup, in some cases, the active alarms would no longer be in sync with the actual alarms affecting the SLA.

Also, a number of other minor fixes with regard to SLA management have been implemented.

#### DataMinerException thrown the first time an InfoData message was deserialized [ID_35897]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

The first time a message with an object of a type that inherited from `InfoData` was sent from SLNet to a client, the following DataMinerException was thrown when the message was deserialized:

```txt
Skyline.DataMiner.Net.Exceptions.DataMinerException: Failed to deserialize message (ProtoBuf). Possible version incompatibility between client and server.  ---&gt; System.InvalidOperationException: It was not possible to prepare a serializer for: Skyline.DataMiner.Net.InfoData ---&gt; System.InvalidOperationException: Unable to resolve a suitable Add method for System.Collections.Generic.IReadOnlyList`1[[System.Guid, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]]&#xD;
```

#### Business Intelligence: Outage correction would incorrectly be increased when a history alarm affected the outage [ID_35942]

<!-- MR 10.4.0 - FR 10.3.5 -->

When a history alarm affected a closed outage to which a correction had been applied, the correction would incorrectly be increased. From now on, the correction will be left untouched.
