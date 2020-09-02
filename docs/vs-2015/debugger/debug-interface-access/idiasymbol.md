---
title: Idiasymmetribol | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c9b267893bacef8c9126b1a17b4eb444af6a1dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692888"
---
# <a name="idiasymbol"></a>IDiaSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beschreibt die Eigenschaften einer Symbol Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>Methoden in alphabetischer Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaSymbol` .  
  
> [!NOTE]
> Symbole geben für einige dieser Methoden sinnvolle Daten zurück, abhängig vom Typ des Symbols. Wenn eine Methode zurückgibt `S_OK` , hat diese Methode sinnvolle Daten zurückgegeben.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Ruft alle untergeordneten Elemente des Symbols ab.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Ruft die untergeordneten Elemente des Symbols ab. Diese Methode ist die erweiterte Version von [idiasymmetribol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Ruft die untergeordneten Elemente des Symbols ab, die an einer angegebenen Adresse gültig sind.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Ruft die untergeordneten Elemente des Symbols ab, die bei einer angegebenen relativen virtuellen Adresse (RVA) gültig sind.|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Ruft die untergeordneten Elemente des Symbols ab, die bei einer angegebenen virtuellen Adresse gültig sind.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer bestimmten Adresse durchlaufen kann.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer angegebenen relativen virtuellen Adresse (RVA) durchlaufen kann.|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer angegebenen virtuellen Adresse (VA) durchlaufen kann.|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in diesem Symbol Inline sind, durchlaufen kann.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in diesem Symbol innerhalb des angegebenen Adress Bereichs angeordnet sind, durchlaufen kann.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt Inline sind, in diesem Symbol innerhalb der angegebenen relativen virtuellen Adresse (RVA) durchlaufen kann.|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt Inline sind, in diesem Symbol innerhalb der angegebenen virtuellen Adresse (VA) durchlaufen kann.|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Wenn ein entsprechender Tagwert angegeben ist, gibt diese Methode eine Enumeration von Symbolen zurück, die in dieser stubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Gibt die Anzahl von Zugriffstasten-Zeiger Tags in einer C++ amp Stub-Funktion zurück.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Gibt alle Accelerator-Zeiger-Tagwerte zurück, die einer C++ amp Accelerator-stubfunktion entsprechen.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Ruft den Zugriffsmodifizierer eines Klassenmembers ab.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Ruft den Offset Teil eines Adress Speicher Orts ab.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Ruft den Abschnitts Teil eines Adress Speicher Orts ab.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Ruft ein Flag ab, das angibt, ob ein anderes Symbol auf diese Adresse verweist.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Ruft den Alters Wert einer Programmdatenbank ab.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Ruft den Symbol Bezeichner des Array Index Typs ab.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Ruft den Array-Indextyp Bezeichner des Symbols ab.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Ruft die Hauptversionsnummer für das Back-End ab.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Ruft die neben Versionsnummer für das Back-End ab.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Ruft die Back-End-Buildnummer ab.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Ruft den Basisdaten Offset ab.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Ruft den Basis Datenslot ab.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Ruft das Symbol ab, auf dem der Zeiger basiert.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Ruft die Symbol-ID ab, auf der der Zeiger basiert.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Ruft das Type-Tag eines einfachen Typs ab.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Ruft die Bitposition eines Speicher Orts ab.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Ruft eine integrierte Art des HLSL-Typs ab.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Gibt einen Indikator für die Aufruf Konvention einer Methode zurück.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Ruft einen Verweis auf die übergeordnete Klasse des Symbols ab.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Ruft den übergeordneten Bezeichner der Klasse des Symbols ab.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Ruft ein Flag ab, das angibt, ob sich das Symbol auf eine Code Adresse bezieht.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Ruft ein Flag ab, das angibt, ob das Symbol vom Compiler generiert wurde.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Ruft den Namen des Compilers ab, der zum Erstellen des [kompianden](../../debugger/debug-interface-access/compiland.md)verwendet wurde.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp über einen Konstruktor verfügt.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Ruft das enthaltende Symbol dieses Symbols ab.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp konstant ist.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Ruft die Anzahl der Elemente in einer Liste oder einem Array ab.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Ruft die Anzahl der gültigen Adressbereiche ab, die dem lokalen Symbol zugeordnet sind.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Ruft ein Flag ab, das angibt, ob die Funktion eine benutzerdefinierte Aufruf Konvention verwendet.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Ruft die Daten Bytes eines OEM-Symbols ab.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Ruft die Variablen Klassifizierung eines Daten Symbols ab.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Ruft das Flag ab, das die Funktionen zum Bearbeiten und Fortfahren des kompilierten Programms oder der kompilierten Einheit beschreibt.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Ruft ein Flag ab, das angibt, ob die Funktion eine weite Rückgabe verwendet.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Ruft die Hauptversionsnummer des Front-Ends ab.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Ruft die neben Versionsnummer des Front-Ends ab.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Ruft die Front-End-Buildnummer ab.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Ruft ein Flag ab, das angibt, ob das öffentliche Symbol auf eine Funktion verweist.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Ruft die GUID des Symbols ab.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Ruft ein Flag ab, das angibt, ob die Funktion einen-aufgerufenen enthält `alloca` .|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Ruft ein Flag ab, das angibt, ob für den benutzerdefinierten Datentyp Zuweisungs Operatoren definiert sind.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Ruft ein Flag ab, das angibt, ob für den benutzerdefinierten Datentyp Umwandlungs Operatoren definiert sind.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Ruft ein Flag ab, das angibt, ob die Kompilierungen Debuginformationen enthält.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Ruft ein Flag ab, das angibt, ob die Funktion über einen Ausnahmehandler im C++-Stil verfügt.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Ruft ein Flag ab, das angibt, ob die Funktion über einen asynchronen Ausnahmehandler verfügt.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Ruft ein Flag ab, das angibt, ob die Funktion über eine Inlineassembly verfügt.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Ruft ein Flag ab, das angibt, ob die Funktion einen longjmp-Befehl enthält (Teil der Ausnahmebehandlung im C-Stil).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Ruft ein Flag ab, das angibt, ob das Modul verwalteten Code enthält.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp über Typdefinitionen verfügt.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Ruft ein Flag ab, das angibt, ob die Funktion oder Kompilierung Sicherheitsüberprüfungen in kompiliert hat (über den [/GS (Buffer Security Check)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) -Compilerschalter).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Ruft ein Flag ab, das angibt, ob die Funktion eine strukturierte Ausnahmebehandlung im Win32-Format aufweist.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Ruft ein Flag ab, das angibt, ob die Funktion einen setjmp-Befehl enthält.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp eine indirekte virtuelle Basisklasse ist.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Ruft ein Flag ab, das angibt, ob die Funktion mit dem Inline-Attribut markiert wurde.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Ruft ein Flag ab, das angibt, ob die Funktion über eine Return from Interrupt-Anweisung verfügt.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Ruft ein Flag ab, das angibt, ob die Funktion die virtuelle Basisklassen Funktion ist.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Ruft ein Flag ab, das angibt, ob das Symbol einer freigegebenen lokalen Variablen einer Gruppe in Code entspricht, der für eine C++ amp Zugriffstaste kompiliert wurde.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Ruft ein Flag ab, das angibt, ob das Symbol dem *Definitions Bereichs Symbol* für die Tagkomponente einer Zeiger Variablen in Code entspricht, der für eine C++ amp Accelerator kompiliert wurde. Das Symbol für den Definitionsbereich ist der Speicherort einer Variablen für eine Adress Spanne.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Gibt an, ob das Symbol einem Funktions Symbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wurde, die einem-Befehl entspricht `parallel_for_each` .|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Ruft ein Flag ab, das angibt, ob die Daten Teil eines Aggregats von vielen Symbolen sind.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Ruft ein Flag ab, das angibt, ob die Symbol Datei C-Typen enthält.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Ruft ein Flag ab, das angibt, ob das Modul von Common Intermediate Language (CIL) in nativen Code konvertiert wurde.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Ruft ein Flag ab, das angibt, ob die Elemente eines benutzerdefinierten Datentyps an einer bestimmten Grenze ausgerichtet sind.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Gibt an, ob dieses Symbol HLSL-Daten (High Level Shader Language) darstellt.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Ruft ein Flag ab, das angibt, ob das Modul mit dem Compilerschalter [/hotpatch (Create Hotpatchable Image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) kompiliert wurde.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Ruft ein Flag ab, das angibt, ob das verwaltete Kompilierungstool mit dem LTCG des Linker verknüpft wurde.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Gibt an, ob die Matrix ein Zeilen Hauptwert ist.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Ruft ein Flag ab, das angibt, ob es sich bei der verwalteten Kompilierungen um eine. netmodule (die nur Metadaten enthält) handelt.|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Gibt `this` an, ob der Zeiger auf einen Datenmember mit Mehrfachvererbung zeigt.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Ruft ein Flag ab, das angibt, ob die Funktion über das [Naked](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) -Attribut verfügt.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Gibt an, ob die Variable entfernt wird.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Gibt an, ob der `this` Zeiger auf einem Symbolwert basiert.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Gibt an, ob dieses Symbol ein Zeiger auf einen Datenmember ist.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Gibt an, ob dieses Symbol ein Zeiger auf eine Element Funktion ist.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Gibt an, ob die Variable einen Rückgabewert enthält.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Gibt an, ob das Modul mit der Option/SDL kompiliert wird.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Gibt `this` an, ob der Zeiger auf einen Datenmember mit einzelner Vererbung zeigt.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Ruft ein Flag ab, das angibt, ob die Daten in ein Aggregat separater Symbole aufgeteilt wurden.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Ruft ein Flag ab, das angibt, ob eine Funktion oder eine Thunk-Ebene statisch ist.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Ruft ein Flag ab, das angibt, ob Private Symbole aus der Symbol Datei entfernt wurden.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Gibt `this` an, ob der Zeiger auf einen Datenmember mit virtueller Vererbung zeigt.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Ruft die Sprache der Quelle ab.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Ruft die Anzahl der Bytes des Arbeitsspeichers ab, die von dem durch dieses Symbol dargestellten Objekt verwendet werden.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Ruft einen Verweis auf das lexikalische übergeordnete Element des Symbols ab.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Ruft den lexikalischen übergeordneten Bezeichner des Symbols ab.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Ruft den Dateinamen der Bibliothek oder der Objektdatei ab, aus der das Objekt geladen wurde.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Gibt die Länge des Adress Bereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Gibt den Abschnitts Teil des Start Adress Bereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Gibt den Offset Teil des Start Adress Bereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Gibt den Anfang des Adress Bereichs zurück, in dem das lokale Symbol gültig ist.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Ruft den Speicherorttyp eines Daten Symbols ab.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Ruft die untere Grenze einer Fortran-Array Dimension ab.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Ruft den Symbol Bezeichner der unteren Grenze einer Fortran-Array Dimension ab.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Ruft den Typ der Ziel-CPU ab.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Ruft ein Flag ab, das angibt, ob das Symbol auf verwalteten Code verweist.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Ruft die Art des Speicherplatzes ab.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Ruft ein Flag ab, das angibt, ob sich das Symbol auf den MSIL-Code (Microsoft Intermediate Language) bezieht.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Ruft den Namen des Symbols ab.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp eingebettet ist.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Ruft ein Flag ab, das angibt, ob die Funktion mit dem [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) -Attribut markiert ist.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Ruft ein Flag ab, das angibt, ob die Funktion mit dem [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) -Attribut deklariert wurde.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Ruft ein Flag ab, das angibt, ob im Rahmen der Stapelpuffer Überprüfung keine Stapel Reihenfolge ausgeführt werden konnte.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Ruft ein Flag ab, das angibt, ob die Funktion oder Bezeichnung niemals erreicht wird.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Gibt die Anzahl von Zugriffstasten-Zeiger Tags in einer C++ amp Stub-Funktion zurück.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Ruft die Anzahl der modifiziererer ab, die auf den ursprünglichen Typ angewendet werden.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Ruft die Anzahl der Registrierungs Indizes ab.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Ruft die Anzahl der Zeilen in der Matrix ab.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Ruft die Anzahl der Spalten in der Matrix ab.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Ruft den Namen der Objektdatei ab.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Ruft den Typ des Objekt Zeigers für eine Klassenmethode ab.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Ruft den Wert des Symbols ab `oemId` .|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Ruft den Wert des Symbols ab `oemSymbolId` .|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Ruft den Offset der Symbol Position ab.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Ruft ein Flag ab, das angibt, ob die Funktion oder Bezeichnung optimierten Code sowie Debuginformationen enthält.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp über überladene Operatoren verfügt.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp gepackt ist.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Ruft den Plattformtyp ab, für den das Programm oder die Kompilierung kompiliert wurde.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Ruft ein Flag ab, das angibt, ob die Funktion rein virtuell ist.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Ruft den Rang eines mehrdimensionalen Fortran-Arrays ab.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Ruft ein Flag ab, das angibt, ob ein Zeigertyp ein Verweis ist.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Ruft den Register Kenn Zeichner des Speicher Orts ab.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Ruft den registriungstyp ab.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse (RVA) des Speicher Orts ab.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Gibt an, ob der `this` Zeiger als eingeschränkt gekennzeichnet ist.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Ruft den samplingslot ab.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp in einem nicht globalen lexikalischen Gültigkeitsbereich angezeigt wird.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Ruft den Signatur Wert des Symbols ab.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Ruft die Größe eines Members eines benutzerdefinierten Typs ab.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Ruft die Slotnummer des Speicher Orts ab.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Ruft den Dateinamen der Quelldatei ab.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Ruft die Quelldatei und die Zeilennummer ab, die angeben, wo ein angegebener benutzerdefinierter Typ definiert ist.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Ruft den Schritt der Matrix oder des stricherten Arrays ab.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Ruft den Untertyp ab.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Ruft die Untertyp-ID ab.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Ruft den Namen der Datei ab, aus der die Symbole geladen wurden.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Ruft den eindeutigen Symbol Bezeichner ab.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Ruft den Symboltyp Klassifizierer ab.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Ruft den Offset Abschnitt eines Thunk-Ziels ab.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Ruft die relative virtuelle Adresse (RVA) eines Thunk-Ziels ab.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Ruft den Adress Abschnitt eines Thunk-Ziels ab.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Ruft die virtuelle Adresse (VA) eines Thunk-Ziels ab.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Ruft den Textur Slot ab.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Ruft die logische-Klasse `this` für die-Methode ab.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Ruft den Thunk-Typ einer Funktion ab.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Ruft den Zeitstempel der zugrunde liegenden ausführbaren Datei ab.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Ruft das Metadatentoken einer verwalteten Funktion oder Variablen ab.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Ruft einen Verweis auf die Funktions Signatur ab.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Ruft den Typbezeichner des Symbols ab.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Ruft ein Array von compilerspezifischen Typwerten für dieses Symbol ab.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Ruft ein Array von compilerspezifischen typbezeichnerwerten für dieses Symbol ab.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Ruft den UAV-Slot ab.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Ruft die Vielfalt eines benutzerdefinierten Typs (User-Defined Type, UDT) ab.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp nicht ausgerichtet ist.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Ruft den nicht ergänzten Namen für einen C++-ergänzten oder-Verknüpfungs Namen ab.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Erweiterung der `get_undecoratedName` Methode, die den nicht ergänzten Namen basierend auf dem Wert eines Erweiterungs Felds abruft.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Ruft die ID des ursprünglichen (unveränderten) Typs ab.|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Ruft die obere Grenze einer Fortran-Array Dimension ab.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Ruft den Symbol Bezeichner der oberen Grenze einer Fortran-Array Dimension ab.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Ruft den Wert einer Konstanten ab.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Ruft ein Flag ab, das angibt, ob die Funktion virtuell ist.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Ruft die virtuelle Adresse (VA) des Speicher Orts ab.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp eine virtuelle Basisklasse ist.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Ruft den Index der virtuellen Basis Verschiebungs Tabelle ab.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Ruft den Offset in der virtuellen Funktions Tabelle einer virtuellen Funktion ab.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Ruft den Offset des virtuellen Basis Zeigers ab.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Ruft den Typ eines virtuellen Basistabellen Zeigers ab.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Ruft die Symbol Schnittstelle des Typs der virtuellen Tabelle für einen benutzerdefinierten Typ ab.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Ruft den Form Bezeichner der virtuellen Tabelle des Symbols ab.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp flüchtig ist.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle auf, indem Sie eine der folgenden Methoden aufrufen:  
  
- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie die lokalen Variablen für eine Funktion an einer angegebenen relativen virtuellen Adresse angezeigt werden. Außerdem wird gezeigt, wie Symbole verschiedener Typen miteinander verknüpft sind.  
  
> [!NOTE]
> `CDiaBSTR` ist eine Klasse, die einen umschließt `BSTR` und automatisch die Freigabe der Zeichenfolge behandelt, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
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
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 `Header:` Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Klassenhierarchie von Symbol Typen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Symbole und Symbol Tags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compiland](../../debugger/debug-interface-access/compiland.md)
