Here are concise ABAP interview questions and answers (1–105). I kept each answer short and practical so you can use them for quick interview prep.

1. What is Check table, value table
- Check table: table used in a foreign key relationship to validate entries of a field (enforces referential integrity).
- Value table: table assigned to a domain (in DDIC) to suggest valid values for F4/help and to be used as authoritative list for a domain.

2. Buffering types
- Full buffering, Generic (group) buffering, Single-record buffering.

3. Types of Control break statements
- AT NEW <field>, AT END OF <field>, AT FIRST, AT LAST (used inside LOOPs or list processing).

4. Difference between Database view and Maintenance view
- Database view: read-only join of DB tables for reporting/queries.
- Maintenance view: created to maintain (insert/update/delete) joined data via generated maintenance screens.

5. Difference between EXPORT and CHANGING in FM
- EXPORTING: parameter sent from FM to caller (output).
- CHANGING: parameter passed bi-directionally; caller’s value can be changed by FM (used for modify-in-place semantics).

6. Interactive reports: primary & secondary list in single page in ALV? How?
- Yes. Use two ALV containers on the same Dynpro or GUI container (CL_GUI_CUSTOM_CONTAINER / CL_GUI_DOCKING_CONTAINER) and in double-click event handler of primary ALV fill/display the secondary ALV in the second container (or use sub-screen to show both).

7. Give list of possible values to input in MPP (Module Pool Programming)? Ways?
- Attach search help (F4) to screen field (DDIC or search help).
- Populate dynamic help using search-help-exit.
- Provide values programmatically in PBO (LOOP AT SCREEN / screen-options) or use popup lists (e.g., CL_GUI_CFW_POPUP).

8. How can we debug the SAPSCRIPT?
- Run the print program that calls the SAPscript and set breakpoints in the driver program or the relevant function modules (OPEN_FORM, WRITE_FORM, CLOSE_FORM). Upload graphic via SE78 then debug the FM that processes the form. Use classical ABAP debugger on the execution.

9. Difference between table and template in Smart Forms (SF). How to create Template?
- Table node: prints tabular rows (repeats for internal table).
- Template (text template): reusable formatted text block.
- Create template inside Smart Forms editor under Text nodes or global definitions; reference it where needed.

10. We are processing either call transaction or session method. Suddenly system is stuck. Then what will happen?
- CALL TRANSACTION: it runs synchronously; if LUW not committed and system crashes, uncommitted database changes are lost; partial effects depend on commits in the transaction.
- Session method (BDC via SM35): if creation succeeded, sessions persist in DB and can be reprocessed later; if processing crashes mid-run, you can reprocess failed sessions from SM35.

11. How can we display the errors in CALL TRANSACTION method?
- Use CALL TRANSACTION ... MESSAGES INTO it_bdcmsgcoll (or using mode 'E') to collect messages into an internal table, then read and display them.

12. When will you choose CALL TRANSACTION & session method?
- CALL TRANSACTION: synchronous, immediate processing, useful for single or interactive runs.
- Session method (BDC via SM35): batch/asynchronous, reliable for mass data loads and reprocessing, auditing via SM35.

13. T.code for Application server? How to upload/download data to/from application server?
- AL11 to view application server directories.
- To upload/download between presentation and application server use CG3Z (upload) and CG3Y (download).
- In ABAP: use OPEN DATASET / TRANSFER for application server; GUI_UPLOAD / GUI_DOWNLOAD for presentation server.

14. T.code for creation of partner profile? Types of messages in IDOC?
- Partner profile: WE20.
- IDoc message types: business message types like ORDERS, INVOIC, MATMAS, DELVRY etc. Also basic type (structure) and segments plus status records.

15. What is ALE? How can you know IDoc reached receiver or not?
- ALE: Application Link Enabling – middleware for distributed SAP systems (IDoc based).
- Check IDoc status in WE02/WE05 (status records) and ports/partner profiles; statuses show success/failure (e.g., 03 processed, 51 error).

16. Few FMs and methods used in OO ALV?
- OO ALV classes: CL_GUI_ALV_GRID, CL_SALV_TABLE, CL_GUI_CUSTOM_CONTAINER. Methods: set_table_for_first_display (CL_GUI_ALV_GRID), get_selected_rows, register_edit_event, refresh_table_display, display. FMs for classical ALV: REUSE_ALV_GRID_DISPLAY.

17. Difference between Abstract class and Interface?
- Abstract class: may contain implemented and abstract methods, attributes, can provide shared code; cannot be instantiated if abstract.
- Interface: only method signatures (no attributes); classes implement interfaces and provide implementations. Interfaces allow multiple inheritance of behavior.

18. Difference between Instance and Static events?
- Instance event: belongs to an object instance; raised by the instance and handled by instance or class handlers.
- Static event (class event): belongs to class level; can be raised without any instance.

19. What is constructor? Difference between instance and static constructor?
- Constructor: method executed on object creation (CONSTRUCTOR).
- Instance constructor: called each time CREATE OBJECT is executed.
- Static/class constructor (CLASS_CONSTRUCTOR): executed once when the class is loaded into memory.

20. What is API? What is RFC? Why we use RFC?
- API: Application Programming Interface – methods/functions offered to interact programmatically.
- RFC: Remote Function Call – protocol to call function modules in remote SAP (or non-SAP) systems.
- Use RFC for system-to-system integration and remote execution (synchronous/asynchronous).

21. Ways to upload data from flat file to SAP system
- GUI_UPLOAD / CL_GUI_FRONTEND_FILE=>GUI_UPLOAD (presentation server).
- OPEN DATASET / TRANSFER (application server).
- BDC / Batch Input, LSMW, BAPI calls, IDoc inbound processing, Directly via ABAP file parsing, or using standard tools (BDC, BAPI, LSMW, SHDB).

22. Difference between BAPI & RFC?
- RFC: protocol to call remote-enabled function modules.
- BAPI: business object API published in BOR; typically implemented as RFC-enabled function modules with standardized parameters and return structure for business object operations.

23. Types of BADIs?
- Classical (older) BADIs and New Enhancement-Framework BADIs. Implementations can be: single-use, multiple-use, and filter-dependent BADIs.

24. What is Enhancement spot, Enhancement framework?
- Enhancement Framework: SAP’s modern enhancement technique (replaces old customer exits) using enhancement points, sections, spots.
- Enhancement spot: container for enhancement options (definitions where implementations can be attached).

25. What is single implementation BADI, multiple implementation BADI?
- Single implementation BADI: only one implementation can be active at runtime.
- Multiple implementation BADI: multiple implementations can be active; system calls them according to configuration / filtering.

26. Performance issues & tools?
- Issues: nested SELECTs, DB calls in loop, unnecessary sorts, huge internal tables, missing indexes.
- Tools: SQL Trace ST05, Runtime Analysis SAT/SE30, Runtime Trace ST12, Code Inspector SCI, SAT, SE30, SM50/SM66, STAD.

27. What is field symbol?
- Runtime pointer to a memory area. Declared with FIELD-SYMBOLS <fs>. Use ASSIGN to reference variables/tables without copying.

28. How can we insert the logo in SAPSCRIPT?
- Upload graphic in SE78, then use command: /: INCLUDE GRAPHICS 'LOGO' in the script or use WRITE_GRAPHIC function modules in the print program.

29. Is it possible to write code in SAPSCRIPT?
- SAPscript supports layout commands and formatting, but not ABAP logic. Put ABAP processing in the driver program; SAPscript only for presentation.

30. How can we insert the logo in ALV Report?
- Load graphic from SE78 and use function modules (e.g., EPS/DSP functions) or include as an image in the print header. In list ALV, use WRITE with graphics (use WRITE_FORM/WRITE_GRAPHIC or convert image to OTF and add).

31. What is AT USER-COMMAND?
- Event triggered by user actions (function key, custom function code) on selection-screen or list screens; used to handle user commands.

32. For MIGO you can attach some fields. If you enter values in those separate fields, where are they saved?
- Data entered in MIGO is saved in material document header/item tables: MKPF (header) and MSEG (items). If custom fields are added via append to these tables, values are stored in those appended columns.

33. Difference between TYPE and LIKE?
- TYPE declares a variable by type name (built-in or DDIC type).
- LIKE declares a variable based on an existing data object or table-field (copies attributes).

34. Difference between REFRESH and FREE?
- REFRESH clears internal table contents but keeps memory allocation.
- FREE clears table and releases memory (table becomes initial).

35. What is search help & lock object?
- Search help: provides F4 value help for fields (DDIC object).
- Lock object: DDIC object that defines enqueue/dequeue mechanism to lock DB entries to avoid parallel updates.

36. What is search help exit?
- A function module (hook) attached to search help that allows custom logic during value help processing (filter/modify values).

37. What is the use of BAPI transaction?
- BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK are used to commit or rollback changes done by BAPI calls; BAPIs perform business operations which may require explicit commit.

38. Types of windows in Smart Forms (SF)?
- Main window, Secondary window, Table window (and page window elements). Main and secondary are most common.

39. How can we handle the double-click event in ALV?
- Register event handler for double_click or hotspot_click on CL_GUI_ALV_GRID or SALV events and handle it in the event handler to display details/secondary ALV.

40. What is the use of CHAIN & ENDCHAIN in MPP?
- CHAIN/ENDCHAIN groups input fields so their validations are processed together at ENDCHAIN (used to delay field validation until ENDCHAIN).

41. What is the purpose of POV & POH in MPP?
- POV: Process On Value — trigger PAI module when a field value changes (value-check).
- POH: Process On Help — trigger processing when help (F4) is requested. (Both are screen field processing attributes.)

42. Differences between BADI & Exits?
- Exits (user exits/customer exits): older, function module/call-back based, limited.
- BADI: object-oriented, more flexible, support multiple implementations, filter-based, part of Enhancement Framework.

43. Scenarios for BADI?
- Use BADIs to implement customer-specific behavior without modifying SAP code (pricing enhancements, custom checks during standard transactions, UI enhancements).

44. How can we know the BADI implementations are active or inactive?
- Check SE19 (BADI implementations) or SE18 to view implementations and their activation status; activation toggled within SE19.

45. How to insert the logo in SF & script? Process flow?
- Upload graphic in SE78 → In Smart Form use Graphics node or include graphic in window/text node → In SAPscript use INCLUDE GRAPHICS 'name' or WRITE_GRAPHIC via driver program → test print.

46. Differences between driver program & report program?
- Driver program: prepares data and calls form (Smart Form/SAPscript) for printing; primarily orchestrates.
- Report program (executable): generates output lists, interactive reports; may also be used as driver.

47. Differences between Main & Variable window?
- Main window: primary window for printing variable content; one main per page area.
- Variable window: in SAPscript, variable-length windows allow text to flow and continue across pages (keeps formatting).

48. In which internal table the messages will store in BDC?
- With CALL TRANSACTION ... MESSAGES INTO it_bdcmsgcoll you get messages in an internal table. For session processing, SM35 session logs store messages; BDCDATA contains BDC data records.

49. Differences among APPEND, INSERT, COLLECT?
- APPEND: add record to end of internal table (or to hashed/sorted appropriate position).
- INSERT: insert record at specified index or into sorted position; can insert into DB table (INSERT DB).
- COLLECT: adds record to internal table and sums numeric fields when record with same key exists (used to aggregate).

50. How we modify the standard DB table structure?
- Don’t modify standard tables directly. Add fields via Append Structure (SE11) or use enhancement / extension technologies (e.g., Customizing include, CT_*). Use Append or include tables provided for customer fields.

51. How can we format the data before WRITE statements in reports?
- Use WRITE options (e.g., WRITE var TO text LENGTH n DECIMALS m), EDIT MASK, CONVERSION_EXITs, or format in ALV fieldcatalog (output length, decimals, edit mask).

52. What is EDI?
- Electronic Data Interchange — exchange of structured business documents (orders/invoices) electronically using standards (EDIFACT, X12); in SAP often implemented via IDocs.

53. What is Test, Persistent, Final, Singleton class?
- Test class: class for ABAP Unit tests (annotated for testing).
- Persistent class: class whose instances can be persisted (Business Object Persistence or persistence mechanism).
- Final class: declared FINAL, cannot be subclassed.
- Singleton: design pattern ensuring a single instance, implemented via private constructor and static get_instance method.

54. What is casting? Different types of casting?
- Casting: converting a reference or value from one type to another.
- Up-casting: subclass → superclass (safe).
- Down-casting: superclass → subclass (requires runtime CHECK using CAST).
- Data casting: CAST operator for data references.

55. What is event? Process for events?
- Event: a signal (in procedural or OO) that something happened. In OO: define EVENT, RAISE EVENT, register handler (CREATE OBJECT / SET HANDLER), implement handler method to respond.

56. How can we insert a table in Module Pool Programming?
- Use Table Control (in Screen Painter) or a subscreen with ALV. Define TABLE control in screen layout and program PBO/PAI logic to fill, display and handle edits.

57. What is sub screen?
- A screen (subscreen) area embedded into a main screen to modularize UI; created with subscreen elements and called using CALL SUBSCREEN in PBO/PAI.

58. Differences between normal screen & sub screen?
- Normal screen: standalone with its own screen number and flow logic.
- Subscreen: embedded within another screen, used as a container; does not run standalone.

59. Pre-requisites for FOR ALL ENTRIES
- Internal table used with FOR ALL ENTRIES must NOT be initial (must have at least one row).
- Use WHERE clauses on key fields.
- Avoid duplicates in internal table (or handle duplicates to avoid extra DB hits).
- Use only SELECT ... FROM ... WHERE <fields>=itab-...; ensure DB table indexes exist for performance.

60. How can we debug the ALE/IDOC?
- Use WE02/WE05 to locate IDoc, check status records, use BD87 to process/reprocess; put breakpoints in inbound function modules (IDOC_INPUT_*) or in partner function modules and run IDoc reprocess under debugger. Use SM58 and SMQ1/SMQ2 for queues.

61. How can we debug the Smart Form?
- Use SSF_FUNCTION_MODULE_NAME to get the generated FM name, then set breakpoints in that FM or use debugger in the print program that calls the Smart Form. You can also test Smart Form in the editor and set breakpoints in global routines.

62. Events TMG? T.Code for TMG?
- TMG = Table Maintenance Generator (utility to generate table maintenance screens).
- T-code/access: Use SE11 → Utilities → Table Maintenance Generator, or directly use SM30 for maintenance.
- Events: table maintenance events include BEFORE_INSERT/AFTER_INSERT, BEFORE_UPDATE, AFTER_UPDATE, etc. Custom logic can be implemented in the Table Maintenance includes (e.g., U* includes).

63. Can we insert any new records in TMG?
- Yes — once TMG is generated for a table, you can insert records via generated maintenance screens (SE16/SM30) if you have authorization and table is not restricted.

64. How can we identify the Customer Exit?
- Use SMOD to list exits, CMOD for implementing them; search for 'EXIT_' includes in code; check enhancement spots/exits in relevant apps via menu or SE80.

65. Process flow of ALV?
- Prepare data → Prepare field catalog → Create container (CL_GUI_CUSTOM_CONTAINER) → Instantiate ALV (CL_GUI_ALV_GRID / CL_SALV_TABLE) → Set layout & event handlers → Display.

66. How many main windows we can create in Smart Form?
- You can have one main window per page area; conceptually one main window is used for flowing content in each page (Smart Forms allow multiple windows but a single main window per page layout).

67. What is Polymorphism?
- Ability of different classes to be treated via a common interface or superclass, methods overridden in subclasses are bound at runtime (dynamic binding).

68. List, Grid display — these two used in OO ABAP?
- OO ALV uses CL_GUI_ALV_GRID for grid displays and SALV (CL_SALV_TABLE) for simplified OO ALV list-like displays; both are available in OO ABAP.

69. Why go for parallel cursor technique?
- To process two internal tables in a single loop using two pointers/cursors to avoid nested loops and improve performance for sorted datasets.

70. Events in Smart Form?
- Initialization (global routines), Form Routines, Page processing, Window processing (before/after), and element-level processing. (Smart Forms also have option to add form routines and initialization nodes.)

71. How can we run the program in background?
- Schedule a job in SM36 or use function modules JOB_OPEN, JOB_SUBMIT, JOB_CLOSE; or SUBMIT <prog> WITH ... VIA JOB.

72. How can we identify the package of transaction?
- Use SE93 to find the program for a transaction, then open program in SE80 or SE11 to see the object and its package; or look up tables TSTC/TSTCT and then program attributes.

73. How can we display barcodes instead of material number in Smart Form?
- Generate barcode image (function modules for barcode or use barcode font) and include it in Smart Form as a graphic or use Smart Form barcode element if available. Configure barcode type and encoding in print.

74. How can we identify the standard BADI?
- Search SE18 for BADI definitions, use repository search for ENH or BADI, or use SAP help / BADI list for the application; check transaction SE84 (Repository Browser) under Enhancement Implementation.

75. How can we identify the standard BAPI?
- Use BAPI Explorer (transaction BAPI) or search in SE37 for RFC-enabled functions and in BOR (BUS2005 etc), or check documentation in SAP help.

76. What are BAPI methods?
- Methods exposed by Business Object Repository (BOR) objects (e.g., CUSTOMER_GETDETAIL, SALESORDER_CREATEFROMDAT2) used to perform business operations on objects.

77. What is Delivery class, data class?
- Delivery class: controls transport and client dependency (A: master data, C: client-dependent customizing, S: system table, etc.).
- Data class: physical area/DB tablespace grouping (master data, transaction, customizing, cluster, pooled).

78. How can we identify the errors?
- Use ST22 (short dumps), SM21 (system log), SLG1 (application log), SM58, SMQS/SMQ2 (q/RFC queues), WE02/WE05 (IDoc), and trace tools like ST05.

79. What are the contents in Technical settings?
- Data class, Size category, Table buffering settings, Logging, Table maintenance settings, Delivery class, and other storage related properties.

80. Why SAPscript is client dependent, SmartForms is independent?
- SAPscript (layout sets) are stored client-dependent in database tables. Smart Forms are stored as repository objects (client independent) and follow different storage semantics. (Result: Smart Forms can be client-independent; scripts historically are client-specific.)

81. How can we hide one field at screen in report and MPP?
- Report/selection-screen: use LOOP AT SCREEN and set SCREEN-ACTIVE = '0' or SCREEN-INVISIBLE = '1' in PBO.
- Module Pool: PBO modify SCREEN table (LOOP AT SCREEN) and set screen-active = 0 or screen-hidden = 1.

82. Difference between structure and table in data dictionary in ABAP?
- Structure: no storage in DB, no key, used for work areas/parameters.
- Table: physical DB storage, has keys, stores data persistently.

83. Difference between COLLECT and SUM?
- COLLECT: used with internal tables to aggregate rows by key and sum numeric fields automatically.
- SUM: arithmetic operator to add values into a numeric variable.

84. How we format the data before WRITE statement in report?
- Use WRITE with formatting options, EDIT MASKs, CONVERSION_EXITs, or pre-format into text via WRITE ... TO <var> USING EDIT MASK.

85. What is the difference between Table and Template?
- Table: structured tabular node for repeating rows (Smart Forms/SAPscript).
- Template: reusable formatted text block for repeated use.

86. When do we use END-OF-SELECTION?
- Use END-OF-SELECTION to process final reporting tasks (e.g., final totals or printing) after start-of-selection and after data selection and list creation are completed.

87. START-OF-SELECTION is default event. When to use it explicitly? Why?
- Use START-OF-SELECTION explicitly when you need to place selection and processing code there to control sequence (e.g., when you have other event blocks like AT SELECTION-SCREEN and want to separate concerns) or when modularizing large reports.

88. Differences between ABAP and OOABAP? When use OOABAP?
- ABAP (procedural): linear programs, function modules.
- OOABAP: encapsulation, inheritance, polymorphism, better for large/reusable systems; prefer OO for interfaces, enhancements, and complex applications.

89. What is table buffer? Which types of tables use this buffer?
- Table buffer: server-side memory caching of table data to reduce DB hits. Used by tables configured with buffering in technical settings: single-record, generic or full buffer enabled tables (typically master data).

90. What is the use of pretty printer?
- Auto-format ABAP source code for consistent indentation and readability.

91. Difference between SAP memory and ABAP memory?
- SAP memory (SET/GET PARAMETER ID, EXPORT TO MEMORY with EXPORT/IMPORT via SAP Memory): global to user session across transactions.
- ABAP memory (EXPORT TO MEMORY/IMPORT FROM MEMORY): local to current internal session/roll area (within same LUW/program chain).

92. Difference between TYPE and LIKE?
- (Repeat of #33) TYPE: declare by type name. LIKE: declare with reference to an existing data object / table-field.

93. What is Tcode SE16? For what is it used? Explain briefly.
- SE16: Data Browser to view table contents and quick searches on DB tables; handy for debugging and checking table data.

94. Difference between dialog program and a report?
- Dialog program: screen-based interactive application using PBO/PAI and screen flow.
- Report: executable program focused on data retrieval and list output; less screen-centric.

95. What is Field symbol?
- (Repeat) Runtime pointer to a data object declared with FIELD-SYMBOLS <fs> and bound with ASSIGN; operates without copying data.

96. How many Main windows we have in Smartforms?
- One main window per page context in the Smart Form layout; you design windows per page and usually one main per page area.

97. Types of windows in Smartforms
- Main window, Secondary window(s), Table windows, and Page windows (definitions for page header/footer etc).

98. How can you find the name of the function module in Smartforms
- Use SSF_FUNCTION_MODULE_NAME to retrieve the generated function module name for a Smart Form, or check the Smart Form editor → Generated Program / Test → see FM name.

99. Difference between Global definitions and Form interface in Smartforms?
- Global definitions: place to declare global variables, data, tables, and form routines used inside the form.
- Form interface: defines IMPORTING, EXPORTING, CHANGING parameters and tables to pass data between driver program and Smart Form.

100. How can you convert Smartform output to PDF?
- Call the Smart Form FM, get OTF data, then use CONVERT_OTF to convert OTF to PDF (CONVERT_OTF followed by CALL FUNCTION 'SCMS_BINARY_TO_XSTRING' / write to file or send as attachment).

101. How can you choose printer name as default in Smartforms?
- Set device parameter when calling the form (PRINT PARAMETERS) or configure default printer for user in SPAD; pass device as argument to the generated FM (preview/print parameters).

102. How can you display the total number of pages in Smartforms?
- Use page number symbols: &PAGE& for current page and &PAGES& or &PAGECOUNT& (depending on template) for total pages; use smart form built-in variables or calculate via OTF conversion and set in a form routine if needed.

103. What is page protection in Smartforms?
- Attributes like “Keep together” or table row pagination settings that prevent splitting elements across pages. Use window/table settings to protect content from being broken.

104. How can you debug the Smartform?
- Use SSF_FUNCTION_MODULE_NAME to get FM, set breakpoints in the generated FM or global routines, and execute form generation under the debugger; you can also set breakpoints in form routines.

105. How can you use barcode in Smartform?
- Use barcode generation function modules or barcode fonts; generate barcode as an image (or use Smart Form’s barcode element if available) and include it in the form. Upload required fonts/graphics in SE78 and configure printing device to support barcode.

If you want, I can:
- Expand any specific answer with code examples (e.g., CALL TRANSACTION MESSAGES INTO usage, example of FOR ALL ENTRIES best practices, example code for CL_GUI_ALV_GRID double-click handler).
- Create a one-page PDF/cheatsheet with these Q&As or a GitHub gist file.

Which topics would you like expanded or to see sample code for?