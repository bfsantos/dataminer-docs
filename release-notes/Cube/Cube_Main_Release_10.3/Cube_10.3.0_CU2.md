---
uid: Cube_Main_Release_10.3.0_CU2
---

# DataMiner Cube Main Release 10.3.0 CU2 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to DataMiner Cube, see [General Main Release 10.3.0 CU1](xref:General_Main_Release_10.3.0_CU2).

### Enhancements

#### Database TTL settings will now be limited to 10 years [ID_35533]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.4 -->

From now on, DataMiner Cube will no longer accept database TTL settings that exceed 10 years.

#### No longer possible to create pattern matching tags that include predicted trend information [ID_35861]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When viewing a trend graph with a trend prediction (i.e. predicted trend information beyond the "Now" line), it will no longer be possible to create pattern matching tags that include predicted trend data.

In other words, when you select a section of a trend graph that is either partly or entirely past the "Now" line, you will not be able to save the tag.

### Fixes

#### Cube could start to consume excessive CPU cycles whenever an operation took a long time or a deadlock occurred [ID_35614]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

Whenever an operation took a long time or a deadlock occurred, up to now, Cube could start to consume excessive CPU cycles.

#### Problems when Cube was configured to connect using gRPC [ID_35615]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When you had configured DataMiner Cube to connect using gRPC (by specifying `type=GRPCConnection` in the *ConnectionSettings.txt* file), the following issues could occur:

- The *About* and *Logging* windows would not be available on the login screen if .NET Remoting had been disabled on the DataMiner Agent.

- In some cases, Cube would become unresponsive when retrieving the user thumbnail pictures. These will now be retrieved in the background.

#### Alarm Console: It could take a long time for an active alarms tab to load on a system with a large number of masked alarms [ID_35843]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

Due to a caching issue, on a system with a large number of masked alarms, it could take a long time for an active alarms tab to load.

#### Alarm Console: Base alarm updates would not be shown when the active alarms tab was filtered [ID_35845]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

In a filtered active alarms tab, in some cases, a base alarm will match the filter while the correlated alarm will not. In that case, the base alarm will be shown while the correlated alarm will not.

However, up to now, when a base alarm was updated, the update would not be reflected in the Alarm Console until the filter was removed.

#### Service & Resource Management: Problem with un-initialized Capacity property on DMAs running version 10.3.1 or 10.2.12 or earlier [ID_35854]

<!-- MR 10.3.0 [CU2] - FR 10.3.2 [CU1] -->

As from DataMiner version 10.3.0/10.3.2, the *Capacity* property is no longer initialized on new resources. As a result, resources without this legacy property would cause server-side issues on DataMiner Agents running either version 10.3.1 or version 10.2.12 or earlier.

From now on, Cube will initialize the *Capacity* property if it detects that the DataMiner Agent is running one of the following versions:

- version 10.3.1 or
- version 10.2.12 or earlier.

#### DataMiner Cube - Visual Overview: [ServiceDefinitionFilter] placeholder would incorrectly not be resolved when used in a table row filter [ID_35923]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When, in a shape data field of type *ParameterControlOptions*, you had specified a table row filter that included a `[ServiceDefinitionFilter]` placeholder (e.g. "TableRowFilter:101=[ServiceDefinitionFilter]"), that placeholder would incorrectly not be resolved, causing the linked table control to be empty when filtered.

#### Spectrum analysis: Problem when opening a spectrum element with an empty username [ID_35927]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

An error could occur when you tried to open a spectrum element of which the username was set to NULL.

Also, an exception could be thrown when you tried to copy spectrum settings to the Windows clipboard.

#### DataMiner Cube - Surveyor: Dragging multiple items from a view card onto a view in the Surveyor did not work as expected [ID_35955]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

Dragging several elements or services from a view card onto a view in the Surveyor did not work as expected.

From now on, when you drag several elements or services from a view card onto a view in the Surveyor

- **the items in that view will be moved** to the view in Surveyor, and
- **the items in any of its sub-views will be copied** to the view in the Surveyor.

If you want to the items in the view to be **copied** to the view in the Surveyor instead of moved, keep the CTRL key pressed while dragging them.
