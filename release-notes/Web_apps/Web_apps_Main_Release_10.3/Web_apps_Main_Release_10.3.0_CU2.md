---
uid: Web_apps_Main_Release_10.3.0_CU2
---

# DataMiner web apps Main Release 10.3.0 CU2 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to the web applications, see [General Main Release 10.3.0 CU2](xref:General_Main_Release_10.3.0_CU2).

### Enhancements

#### Monitoring app: Elements, services and views opened by clicking a Visio shape will open in the same tab instead of a new tab [ID_35781]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

In the *Monitoring* app, from now on, elements, services and views opened by clicking a Visio shape will open in the same tab instead of a new tab.

#### Web apps - Query builder: Query node options with only a single value will no longer be displayed in a selection box [ID_35865]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

In the query builder, from now on, when a query node option only has a single value, that option will no longer be displayed in a selection box.

For example, up to now, when you selected the *Get elements* data source, followed by the *Aggregate* operator, the method selection box would display "Get the". This will no longer be the case.

#### Web apps: Enhanced error handling when executing an interactive Automation script by clicking a DOM button [ID_35909]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

Overall error handling has been improved when executing an interactive Automation script by clicking a DOM button in a web app.

### Fixes

#### Dashboards app: Sticky component menus would no longer be fully visible after you had changed the number of dashboard columns [ID_35702]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.4 -->

Sticky component menus would no longer be fully visible after you had changed the number of dashboard columns.

#### Dashboards app & low-code apps: GQI components would incorrectly not clear their query row feed when refetching data [ID_35767]

<!-- MR 10.3.0 [CU2] - FR 10.3.4 -->

GQI components would incorrectly not clear their query row feed when refetching data.

#### Dashboards app & Low-code apps - GQI components: Problem when executing an empty query [ID_35803]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When GQI components tried to execute an empty query, up to now, they would keep on showing a "loading" indicator. From now on, an appropriate message will be displayed instead.

#### Dashboards app & Low-code apps: Duplicated component would not have the size as the original [ID_35804]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When you duplicated a component, the size of the duplicate would incorrectly be limited to 30 rows. From now on, when you duplicate a component, the duplicate will have the same size as the original.

#### Dashboards app: Problem when using the search box on a mobile device [ID_35825]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When the *Dashboards* app was opened on a mobile device, an error could occur when you entered something in the search box.

#### Dashboards app & Low-code apps - Form component: Problems with multiple-selection drop-down boxes [ID_35829]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When a form component contained multiple-selection drop-down boxes, it would load too slowly due to the drop-down box change detection being triggered over and over again. From now on, form components containing multiple-selection drop-down boxes will load considerably quicker.

Also, when a multiple-selection drop-down field of a DOM instance was added to a form component, the current values preloaded into the field as placeholders would incorrectly not get removed once the data was loaded, causing the drop-down field to contain duplicate values.

#### Dashboards app: A table component could appear to be empty when you rapidly switched between visualizations [ID_35831]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

In some cases, a table component could appear to be empty when you rapidly switched between visualizations.

Also, an error could be thrown when you tried to add an invalid query to a component.

#### Web apps: Problem when opening a visual overview [ID_35841]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

When you opened a visual overview in a web app, in some cases, the web app could become unresponsive.

#### Dashboards app & Low-code apps: Text boxes in the Layout tab would not update when you selected another component [ID_35851]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When, in the *Layout* tab, a text box (e.g. the box containing the title of the selected component) had the focus, and you selected another component, the text box in the *Layout* tab would incorrectly still contain the value of the previously selected component.

#### Dashboards app & Low-code apps - Table component: A collapsed group would incorrectly expand when new data was loaded into the table [ID_35856]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When, in a table component, the data was grouped by two different parameters, in some cases, a collapsed group would incorrectly expand when new data was loaded into the table.

#### Dashboards app: Multiple parameter feeds would incorrectly have their 'group by' reset when a PDF was generated [ID_35866]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

When you generated a PDF of a dashboard that contained multiple parameter feeds, a multiple parameter feed with a "group by" applied would incorrectly have that "group by" reset to the value that was configured in its settings.

#### Web apps: Certain icons would incorrectly not be displayed [ID_35877]

<!-- MR 10.2.0 [CU13]/10.3.0 [CU2] - FR 10.3.5 -->

In web apps, certain icons would incorrectly not be displayed.

#### Dashboards app & Low-code apps - Table component: Initial grouping would incorrectly be considered a modification [ID_35882]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

In a table component, the initial grouping would incorrectly be considered a modification. As a result, the *Restore initial view* button would appear in the component header. When you then clicked that button, the grouping would be removed.

From now on, the initial grouping will no longer be considered a modification. When you modify the table by sorting, filtering, grouping or re-ordering data and then click the *Restore initial view* button, the initial grouping will now be restored.

#### Dashboards app & Low-code apps - Table component: Issues with 'Loading' indicator [ID_35894]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

A number of issues with regard to the "Loading" indicator have been fixed.

#### Dashboards app & Low-code apps - GQI: Queries linked to feeds would not always apply feed changes [ID_35903]

<!-- MR 10.3.0 [CU2] - FR 10.3.4 [CU0] -->

In some cases, a query that was linked to feeds would not apply the feed changes in the visualizations unless it was opened in edit mode.

#### Web apps: Login button would incorrectly be disabled on Edge and Chrome [ID_35906]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

Up to now, in some cases, the login button would incorrectly be disabled when you opened a web app in Microsoft Edge or Google Chrome.

#### Dashboards app & Low-code apps - Clock components: Clock time would not update when set to server time [ID_35912]

<!-- MR 10.2.0 [CU14]/10.3.0 [CU2] - FR 10.3.5 -->

When a clock component (analog or digital) was set to use server time, the clock time would not update.

#### Low-code apps: Problem when selecting an action with multiple components after having selected an action with a single component [ID_35947]

<!-- MR 10.3.0 [CU2] - FR 10.3.5 -->

When you first selected an action with a single component, which was selected automatically, and then selected an action with multiple components, up to now, both the action selection box and the component selection box would incorrectly be cleared.
