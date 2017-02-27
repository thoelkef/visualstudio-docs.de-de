---
title: "IDiaSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol-Schnittstelle"
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# IDiaSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Beschreibt die Eigenschaften einer Symbolinstanz.  
  
## Syntax  
  
```  
IDiaSymbol : IUnknown  
```  
  
## Methoden in alphabetischer Reihenfolge  
 Die folgende Tabelle zeigt die `IDiaSymbol`\-Methoden.  
  
> [!NOTE]
>  Symbole geben sinnvolle Daten nur für einige dieser Methoden zurück, je nach Art des Symbols.  Wenn eine Methode `S_OK` zurückgibt, dann hat diese Methode aussagekräftige Daten zurückgegeben.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Ruft alle untergeordneten Elemente des Symbols ab.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Ruft die untergeordneten Elemente des Symbols ab.  Diese Methode ist die erweiterte Version von [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Ruft die untergeordneten Elemente des Symbols ab, die an einer angegebenen Adresse gültig sind.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Ruft die untergeordneten Elemente des Symbols ab, die an einer angegebenen relativen virtuellen Adresse gültig sind.|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Ruft die untergeordneten Elemente des Symbols ab, die an einer angegebenen virtuellen Adresse gültig sind.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen Adresse zu durchlaufen.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen relativen virtuellen Adresse RVA \(\) zu durchlaufen.|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen virtuellen Adresse \(VA\) zu durchlaufen.|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in diesem Symbol.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in diesem Symbol im angegebenen Adressbereichs.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in diesem Symbol in der angegebenen relativen virtuellen Adresse RVA \(\).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in diesem Symbol in der angegebenen virtuellen Adresse \(VA\).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Erstellen eines entsprechenden Tagwert angegeben, gibt diese Methode eine Enumeration von Symbolen zurück, die in dieser Stubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Gibt die Anzahl der Zugriffstastenzeigertags in der AMP\-Stubfunktion einer C\+\+\-Datei zurück.|  
|[IDiaSymbol::get\_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Gibt alle Zugriffstastenzeigertagwerte zurück, die zur AMPzugriffstasten\-Stubfunktion einer C\+\+\-Datei entsprechen.|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Ruft den Zugriffsmodifizierer eines Klassenmembers ab.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Ruft den Offsetteil einer Adresse ab.|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Ruft den Abschnittsteil einer Adresse ab.|  
|[IDiaSymbol::get\_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Ruft ein Flag ab, das angibt, ob ein anderes Symbol diese Adresse referenziert.|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Ruft den Wert des Alters einer Programmdatenbank ab.|  
|[IDiaSymbol::get\_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Ruft den Symbolbezeichner des Arrayindextyps ab.|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Ruft den Bezeichner des Arrayindextyps für das Symbol ab.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Ruft die Back\-End\-Hauptversionsnummer ab.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Ruft die Back\-End\-Nebenversionsnummer ab.|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Ruft die Back\-End\-Buildnummer ab.|  
|[IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Ruft den Datenoffset ab.|  
|[IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Ruft den grundlegenden Datenslot ab.|  
|[IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Ruft das Symbol ab, von dem der Zeiger basiert.|  
|[IDiaSymbol::get\_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Ruft die Symbol ID ab, von der der Zeiger basiert.|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Ruft das Typtag eines einfachen Typs ab.|  
|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Ruft die Bitposition eines Speicherorts ab.|  
|[IDiaSymbol::get\_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Ruft eine integrierte Art HLSL\-Typ ab.|  
|[IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Gibt einen Indikator einer Methodenaufrufkonvention zurück.|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Ruft einen Verweis auf die dem Symbol übergeordnete Klasse ab.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Ruft den übergeordneten Klassenbezeichner des Symbols ab.|  
|[IDiaSymbol::get\_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Ruft ein Flag ab, das angibt, ob das Symbol auf eine Codeadresse verweist.|  
|[IDiaSymbol::get\_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Ruft ein Flag ab, das angibt, ob das Symbol vom Compiler generiert wurde.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Ruft den Namen des Compilers ab, der verwendet wird, um [Compiland](../../debugger/debug-interface-access/compiland.md) zu erstellen.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp über einen Konstruktor verfügt.|  
|[IDiaSymbol::get\_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Ruft das enthaltende Symbol dieses Symbols ab.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp konstant ist.|  
|[IDiaSymbol::get\_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Ruft die Anzahl der Elemente in einer Liste oder einem Array ab.|  
|[IDiaSymbol::get\_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Ruft die Anzahl der gültigen Adressbereiche ab, die dem lokalen Symbol zugeordnet sind.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Ruft ein Flag ab, ob die Funktion eine benutzerdefinierte Aufrufkonvention verwendet.|  
|[IDiaSymbol::get\_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Ruft die Datenbytes eines OEM\-Symbols ab.|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Ruft die variable Klassifizierung eines Datensymbols ab.|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Ruft das Flag ab, das die Funktionen zum Bearbeiten und Fortfahren für das kompilierte Programm bzw. die kompilierte Einheit beschreibt.|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Ruft ein Flag ab, ob die Funktion ein weit beendet werden verwendet.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Ruft die Front\-End\-Hauptversionsnummer ab.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Ruft die Front\-End\-Nebenversionsnummer ab.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Ruft die Front\-End\-Buildnummer ab.|  
|[IDiaSymbol::get\_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Ruft ein Flag ab, das angibt, ob das öffentliche Symbol auf eine Funktion verweist.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Ruft die GUID des Symbols ab.|  
|[IDiaSymbol::get\_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Ruft ein Flag ab, ob die Funktion einen Aufruf `alloca` enthält.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Ruft ein Flag ab, das angibt, ob für den benutzerdefinierten Datentyp Zuweisungsoperatoren definiert sind.|  
|[IDiaSymbol::get\_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Ruft ein Flag ab, das angibt, ob für den benutzerdefinierten Datentyp Umwandlungsoperatoren definiert sind.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Ruft ein Flag ab, ob die Kompiliereinheit alle Debuginformationen enthält.|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Ruft ein Flag ab, ob die Funktion Ausnahmehandler eine \+\+\-style verfügt.|  
|[IDiaSymbol::get\_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Ruft ein Flag ab, ob die Funktion einen asynchronen Ausnahmehandler enthält.|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Ruft ein Flag ab, ob die Funktion Inlineassembly verfügt.|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Ruft ein Flag ab, ob die Funktion einen longjmp Befehl enthält \(Teil Ausnahmebehandlung im C\-Format\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Ruft ein Flag ab, das angibt, ob das Modul verwalteten Code enthält.|  
|[IDiaSymbol::get\_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp Definitionen des geschachtelten Typs enthält.|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Ruft ein Flag ab, das angibt, ob die Funktion oder die Kompiliereinheit die Sicherheitsüberprüfungen verfügt, die in kompiliert \(über den [\/GS \(Puffer\-Sicherheitsüberprüfung\)](/visual-cpp/build/reference/gs-buffer-security-check) Compilerschalter\).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Ruft ein Flag ab, ob die Funktion Win32\-Anwendungsmanifest strukturierte Ausnahmebehandlung verfügt.|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Ruft ein Flag ab, ob die Funktion einen setjmp Befehl enthält.|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp eine indirekte virtuelle Basisklasse ist.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Ruft ein Flag ab, ob die Funktion inline mit dem Attribut markiert wurde.|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Ruft ein Flag ab, ob die Funktion eine Rückgabe von der Unterbrechungsanweisung verfügt.|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Ruft ein Flag ab, das angibt, ob die Funktion die virtuelle Funktion der Basisklasse ist.|  
|[IDiaSymbol::get\_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Ruft ein Flag ab, das angibt, ob das Symbol zu einer Gruppe freigegebenen lokalen Variable im Code entspricht, der Zugriffstaste für AMP in C\+\+ kompiliert wird.|  
|[IDiaSymbol::get\_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Ruft ein Flag ab, das angibt, ob das Symbol zum *Definitionsbereichssymbol* für die Tagkomponente einer Zeigervariable im Code entspricht, der Zugriffstaste für AMP in C\+\+ kompiliert wird.  Das Definitionsbereichssymbol Speicherort einer Variable für eine Spanne von Adressen.|  
|[IDiaSymbol::get\_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Gibt an, ob das Symbol in einen Funktionssymbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wird, die einem `parallel_for_each` Aufruf entspricht.|  
|[IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Ruft ein Flag ab, ob die Daten Teil eines Aggregats vieler Symbole sind.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Ruft ein Flag ab, ob die Symboldatei C enthält.|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Ruft ein Flag ab, ob das Modul von der allgemeinen Intermediate Language \(CIL\) in systemeigenen Code konvertiert wurde.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Ruft ein Flag ab, ob die Elemente eines benutzerdefinierten Datentyps zu einer bestimmten Begrenzung ausgerichtet sind.|  
|[IDiaSymbol::get\_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Gibt an, ob dieses Symbol Daten High\-Level Shader Languages \(HLSL\) darstellt.|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Ruft ein Flag ab, das angibt, ob das Modul mit dem [\/hotpatch \(Erstellen eines Hotpatch\-fähigen Abbildes\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image)\-Compilerschalter kompiliert wurde.|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Ruft ein Flag ab, ob die verwaltete Kompiliereinheit mit dem LTCG des Linkers verknüpft wurde.|  
|[IDiaSymbol::get\_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Gibt an, ob die Matrix Zeilenmajor ist.|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Ruft ein Flag ab, ob die verwaltete Kompiliereinheit A. ist.  netmodule \(nur Metadaten enthalten\).|  
|[IDiaSymbol::get\_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Gibt an, ob der `this` Zeiger auf einen Datenmember mit Mehrfachvererbung zeigt.|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Ruft ein Flag ab, ob die Funktion [naked](/visual-cpp/cpp/naked-cpp) das Attribut verfügt.|  
|[IDiaSymbol::get\_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Gibt an, ob die Variable weg optimiert ist.|  
|[IDiaSymbol::get\_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Gibt an, ob der `this` Zeiger auf Grundlage eines Symbolwert ist.|  
|[IDiaSymbol::get\_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Gibt an, ob dieses Symbol ein Zeiger auf einen Datenmember ist.|  
|[IDiaSymbol::get\_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Gibt an, ob dieses Symbol ein Zeiger auf eine Memberfunktion ist.|  
|[IDiaSymbol::get\_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Gibt an, ob die Variable einen Rückgabewert enthält.|  
|[IDiaSymbol::get\_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Gibt an, ob das Modul mit der Option \/SDL\- kompiliert wird.|  
|[IDiaSymbol::get\_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Gibt an, ob der `this` Zeiger auf einen Datenmember mit einzelner Vererbung zeigt.|  
|[IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Ruft ein Flag ab, ob die Daten in ein Aggregat von separaten Symbolen geteilt wurden.|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Ruft ein Flag ab, das angibt, ob eine Funktion\- oder eine Thunkebene statisch ist.|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Ruft ein Flag ab, ob private Symbole aus der Symboldatei entfernt wurden.|  
|[IDiaSymbol::get\_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Gibt an, ob der `this` Zeiger auf einen Datenmember mit virtueller Vererbung zeigt.|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Ruft die Sprache der Quelle ab.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Ruft die Anzahl der Bytes des Arbeitsspeichers ab, die von dem Objekt verwendet werden, das durch dieses Symbol dargestellt wird.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Ruft einen Verweis auf das dem Symbol übergeordnete lexikalische Element ab.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Ruft den übergeordneten lexikalischen Bezeichner des Symbols ab.|  
|[IDiaSymbol::get\_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Ruft den Dateinamen der Bibliothek oder Objektdatei ab, aus der das Objekt geladen wurde.|  
|[IDiaSymbol::get\_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Gibt die Länge des Adressbereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Gibt den Abschnittsteil des Startadressenbereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get\_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Gibt den Offsetteil des Startadressenbereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get\_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Gibt den Anfang des Adressbereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Ruft den Positionstyp eines Datensymbols ab.|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Ruft die untere Grenze einer FORTRAN\-Arraydimension ab.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Ruft den Symbolbezeichner der unteren Grenze einer FORTRAN\-Arraydimension ab.|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Ruft den Typ des CPU\-Ziels ab.|  
|[IDiaSymbol::get\_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Ruft ein Flag ab, das angibt, ob sich das Symbol auf verwalteten Code bezieht.|  
|[IDiaSymbol::get\_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Ruft die Speicherbereichsart ab.|  
|[IDiaSymbol::get\_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Ruft ein Flag ab, das angibt, ob das Symbol auf MSIL\-Code \(Microsoft Intermediate Language\) verweist.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Ruft den Namen des Symbols ab.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp geschachtelt ist.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Ruft ein Flag ab, ob die Funktion mit dem [noinline](/visual-cpp/cpp/noinline)\-Attribut markiert ist.|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Ruft ein Flag ab, ob die Funktion mit dem [noreturn](/visual-cpp/cpp/noreturn)\-Attribut deklariert wurde.|  
|[IDiaSymbol::get\_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Ruft ein Flag ab, dass keine Stapelreihenfolge als Teil der Stapelpufferüberprüfung durchgeführt werden kann.|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Ruft ein Flag ab, ob die Funktion oder die Bezeichnung nie erreicht wird.|  
|[IDiaSymbol::get\_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Gibt die Anzahl der Zugriffstastenzeigertags in der AMP\-Stubfunktion einer C\+\+\-Datei zurück.|  
|[IDiaSymbol::get\_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Ruft die Anzahl der Modifizierern ab, die dem ursprünglichen Typ angewendet werden.|  
|[IDiaSymbol::get\_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Ruft die Anzahl der Registerindizes ab.|  
|[IDiaSymbol::get\_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Ruft die Anzahl der Zeilen in der Matrix ab.|  
|[IDiaSymbol::get\_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Ruft die Anzahl der Spalten in der Matrix ab.|  
|[IDiaSymbol::get\_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Ruft den Objektdateinamen ab.|  
|[IDiaSymbol::get\_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Ruft den Typ des Objektzeigers für eine Klassenmethode ab.|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Ruft den `oemId`\-Wert des Symbols ab.|  
|[IDiaSymbol::get\_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Ruft den `oemSymbolId`\-Wert des Symbols ab.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Ruft den Offset des Symbolspeicherorts ab.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Ruft ein Flag ab, ob die Funktion oder die Bezeichnung optimierten Code sowie Debuginformationen enthält.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp über überladene Konstruktoren verfügt.|  
|[IDiaSymbol::get\_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp gepackt ist.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Ruft den Typ der Plattform ab, für die das Programm oder die Kompiliereinheit kompiliert wurde.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Ruft ein Flag ab, das angibt, ob die Funktion rein virtuell ist.|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Ruft den Rang eines mehrdimensionalen FORTRAN\-Arrays ab.|  
|[IDiaSymbol::get\_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Ruft ein Flag ab, das angibt, ob ein Zeigertyp ein Verweis ist.|  
|[IDiaSymbol::get\_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Ruft den Registerkennzeichner des Speicherorts ab.|  
|[IDiaSymbol::get\_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Ruft das Register ab.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse \(RVA\) des Speicherorts ab.|  
|[IDiaSymbol::get\_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Gibt an, ob der `this` Zeiger bezeichnet wird, wie beschränkt.|  
|[IDiaSymbol::get\_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Ruft den Samplerslot ab.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp in einem nichtglobalen lexikalischen Gültigkeitsbereich angezeigt wird.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Ruft den Signaturwert des Symbols ab.|  
|[IDiaSymbol::get\_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Ruft die Größe eines Members eines benutzerdefinierten Typs ab.|  
|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Ruft die Slotnummer der Position ab.|  
|[IDiaSymbol::get\_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Ruft den Dateinamen der Quelldatei ab.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Ruft die Quelldatei und die Zeilennummer ab, die angeben, wo ein angegebener benutzerdefinierter Typ definiert ist.|  
|[IDiaSymbol::get\_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Ruft den Schritt der Matrix oder des strided Arrays ab.|  
|[IDiaSymbol::get\_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Ruft den Vortyp ab.|  
|[IDiaSymbol::get\_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Ruft die ID ab Vortyp|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Ruft den Namen der Datei ab, aus der die Symbole geladen wurden.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Ruft den eindeutigen Bezeichner des Symbols ab.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Ruft den Symboltypklassifizierer ab.|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Ruft den Offsetteil eines Thunkziels ab.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Ruft die relative virtuelle Adresse eines Thunkziels ab.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Ruft den Adressteil eines Thunkziels ab.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Ruft die virtuelle Adresse eines Thunkziels ab.|  
|[IDiaSymbol::get\_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Ruft den Beschaffenheitsslot ab.|  
|[IDiaSymbol::get\_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Ruft das logische `this`\-Anpassungselement für die Methode ab.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Ruft den Thunktyp einer Funktion ab.|  
|[IDiaSymbol::get\_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Ruft den Zeitstempel der zugrunde liegenden ausführbaren Datei ab.|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Ruft das Metadatentoken für eine verwaltete Funktion oder Variable ab.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Ruft einen Verweis auf die Funktionssignatur ab.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Ruft den Typenbezeichner des Symbols ab.|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Ruft ein Array von compilerspezifischen Typwerten für dieses Symbol ab.|  
|[IDiaSymbol::get\_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Ruft ein Array von compilerspezifischen Typbezeichnerwerten für dieses Symbol ab.|  
|[IDiaSymbol::get\_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Ruft den uav\-Slot ab.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Ruft die Auswahl für einen benutzerdefinierten Typ ab.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp nicht ausgerichtet ist.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Ruft den nicht ergänzten Namen für einen ergänzten C\+\+\-Namen \(oder Bindungsnamen\) ab.|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Erweiterung der `get_undecoratedName`\-Methode, die den nicht ergänzten Namen auf Grundlage des Werts eines Erweiterungsfeldes abruft.|  
|[IDiaSymbol::get\_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Ruft die ID des ursprünglichen \(unveränderten\) Typ ab.|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Ruft die obere Grenze einer FORTRAN\-Arraydimension ab.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Ruft den Symbolbezeichner der oberen Grenze einer FORTRAN\-Arraydimension ab.|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Ruft den Wert einer Konstanten ab.|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Ruft ein Flag ab, das angibt, ob die Funktion virtuell ist.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Ruft die virtuelle Adresse des Speicherorts ab.|  
|[IDiaSymbol::get\_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp eine virtuelle Basisklasse ist.|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Ruft den Index für die virtuelle Basisverschiebungstabelle ab.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Ruft den Offset in der virtuellen Funktionstabelle einer virtuellen Funktion ab.|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Ruft den Offset des virtuellen Basiszeigers ab.|  
|[IDiaSymbol::get\_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Ruft den Typ eines virtuellen Basistabellenzeigers ab.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Ruft die Symboloberfläche des Typs der virtuellen Tabelle für einen benutzerdefinierten Typ ab.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Ruft den Formbezeichner der virtuellen Tabelle für das Symbol ab.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp veränderlich ist.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle ab, indem Sie eine der folgenden Methoden aufrufen:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die lokalen Variablen für eine Funktion an der angegebenen relativen virtuellen Adresse angezeigt werden.  Darüber hinaus wird gezeigt, wie Symbole verschiedener Typen miteinander verknüpft sind.  
  
> [!NOTE]
>  `CDiaBSTR` ist eine Klasse, die ein `BSTR` umbricht und automatisch die Freigabe der Zeichenfolge behandelt, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## Anforderungen  
 `Header:` Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compiland](../../debugger/debug-interface-access/compiland.md)