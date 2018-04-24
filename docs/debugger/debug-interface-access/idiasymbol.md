---
title: IDiaSymbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a456abd2d3d80a122d4182ae882ca28b07788596
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbol"></a>IDiaSymbol
Beschreibt die Eigenschaften einer Instanz des Symbols.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>Methoden in alphabetischer Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaSymbol`.  
  
> [!NOTE]
>  Symbole gibt sinnvolle Daten nur für einige dieser Methoden, abhängig vom Typ des Symbols zurück. Wenn eine Methodenrückgabe `S_OK`, wird diese Methode sinnvolle Daten zurückgegeben hat.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Ruft alle untergeordneten Elemente des Symbols ab.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Ruft die untergeordneten Elemente des Symbols ab. Diese Methode ist die erweiterte Version des [idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Ruft die untergeordneten Elemente des Symbols, die an einer bestimmten Adresse gültig sind.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Ruft die untergeordneten Elemente des Symbols, die bei einem angegebenen relativen virtuellen Adresse (RVA) gültig sind.|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Ruft die untergeordneten Elemente des Symbols, die an einer bestimmten virtuellen Adresse gültig sind.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Ruft eine Enumeration, die von einem Client zum iterieren durch alle Inlineframes auf einer angegebenen Adresse ermöglichen.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Ruft eine Enumeration, die von einem Client zum iterieren durch alle Inlineframes auf einer angegebenen relativen virtuellen Adresse (RVA) ermöglichen.|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Ruft eine Enumeration, die einen Client zum iterieren durch alle Inlineframes auf einer bestimmten virtuellen Adresse ("VA" ist) ermöglicht.|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Ruft eine Enumeration, die ermöglicht einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in dieses Symbols ab.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in dieses Symbol in der angegebenen Adressbereich ab.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in dieses Symbol innerhalb der angegebenen relativen virtuellen Adresse (RVA) ab.|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in dieses Symbol innerhalb der angegebenen virtuellen Adresse ("VA" ist).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Wenn einen entsprechenden Tagwert, gibt diese Methode eine Enumeration von Symbolen, die enthalten sind in dieser Stub-Funktion auf einem angegebenen relativen virtuellen Adresse an.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Gibt die Anzahl der Zugriffstaste Zeiger Tags in einer C++ AMP-Stub-Funktion zurück.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Gibt alle Accelerator Zeiger Tagwert aufweisen, die entsprechen einer C++ AMP-Beschleuniger Stub-Funktion zurück.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Ruft den Zugriffsmodifizierer eines Klassenmembers ab.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Ruft den Zeitzonenoffset-Teil eines Speicherorts Adresse ab.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Ruft den Abschnitt Teil einer Adressspeicherort ab.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Ruft ein Flag, das angibt, ob ein anderes Symbol diese Adresse verweist.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Ruft den Age-Wert, der eine Programmdatenbank ab.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Ruft die Symbol-ID des Indextyps Array ab.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Ruft das Array Index Typbezeichner des Symbols ab.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Ruft die Back-End-Hauptversionsnummer.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Ruft die Back-End-Nebenversionsnummer ab.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Ruft die Anzahl der Back-End-Build.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Ruft den Offset für die Basisdaten ab.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Ruft die Basisdaten Slot ab.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Ruft das Währungssymbol aus dem der Zeiger ist.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Ruft die Symbol-ID, die von dem der Zeiger basiert.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Ruft den Typ-Tags eines einfachen Typs ab.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Ruft die Bitposition des Speicherorts ab.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Ruft eine integrierte Art des HLSL-Typs ab.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Gibt einen Indikator für die Aufrufkonvention einer Methode zurück.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Ruft einen Verweis auf die übergeordnete Klasse des Symbols ab.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Ruft den übergeordneten Klassenbezeichner des Symbols ab.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Ruft ein Flag, der angibt, ob das Symbol auf einer Codeadresse verweist.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Ruft ein Flag, das angibt, ob das Symbol vom Compiler generierte wurde ab.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Ruft den Namen des Compilers zum Erstellen der [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp einen Konstruktor verfügt.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Ruft das enthaltende Symbol dieses Symbols ab.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp konstant ist.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Ruft die Anzahl der Elemente in einer Liste oder Array ab.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Ruft die Anzahl der gültigen Adressbereiche, die mit der lokalen Symbolcache zugeordnet.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Ruft ein Flag, das angibt, ob die Funktion eine benutzerdefinierte-Aufrufkonvention verwendet.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Ruft die Datenbytes, die von einem OEM-Symbol ab.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Ruft die Variable Klassifizierung eines Daten-Symbols ab.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Ruft das Flag, beschreibt die Funktionen für bearbeiten und Fortfahren das kompilierte Programm oder Einheit ab.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Ruft ein Flag, das angibt, ob die Funktion eine weit return verwendet.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Ruft die Front-End-Hauptversionsnummer.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Ruft die Front-End-Nebenversionsnummer ab.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Ruft die Anzahl der Front-End-Build.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Ruft ein Flag, der angibt, ob die öffentlichen Symboldateien an eine Funktion verweist.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Ruft das Symbol GUID ab.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Ruft ein Flag, das angibt, ob die Funktion einen Aufruf enthält `alloca`.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp alle Zuweisungsoperatoren definiert wurde.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp alle Umwandlungsoperatoren definiert wurde.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Ruft ein Flag, das angibt, ob der Kompiliereinheit alle Debuginformationen ab.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Ruft ein Flag, das angibt, ob die Funktion einen Ausnahmehandler im C++-Format aufweist.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Ruft ein Flag, das angibt, ob die Funktion einen Handler für asynchrone Ausnahmen aufweist.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Ruft ein Flag, das angibt, ob die Funktion Inlineassembly hat.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Ruft ein Flag, das angibt, ob die Funktion ein Longjmp-Befehl (Teil der Ausnahmebehandlung im C-Format) enthält.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Ruft ein Flag, das angibt, ob das Modul verwalteten Code enthält.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp Typdefinitionen geschachtelte ab.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Ruft ein Flag, das angibt, ob die Funktion oder Kompiliereinheit sicherheitsüberprüfungen im kompilierten hat (über die [/GS (Puffer-Sicherheitsüberprüfung)](/cpp/build/reference/gs-buffer-security-check) Compilerschalter).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Ruft ein Flag, das angibt, ob die Funktion strukturierte Ausnahmebehandlung im Win32-Format hat ab.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Ruft ein Flag, das angibt, ob die Funktion ein Setjmp-Befehl enthält.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp eine indirekte Basisklasse ist.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Ruft ein Flag, das angibt, ob die Funktion mit dem Inline-Attribut markiert wurde.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Ruft ein Flag, das angibt, ob die Funktion eine Rückgabe von Interrupt-Anweisung hat.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Ruft ein Flag, das angibt, ob die Funktion der virtuellen Funktion der Basisklasse ist.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Ruft ein Flag, das angibt, ob das Symbol auf die freigegebene lokale Gruppenvariable im Code für einen C++-AMP-Beschleuniger kompiliert entspricht.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Ruft ein Flag, das angibt, ob das Symbol entspricht der *Definition Bereich Symbol* für die Tag-Komponente einer Zeigervariablen im Code für einen C++-AMP-Beschleuniger kompiliert. Die Definition Bereich Symbol ist der Speicherort einer Variablen für einen Textabschnitt Adressen.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Gibt an, ob das Symbol entspricht ein Symbol für die Funktion der obersten Ebene für einen Shader kompiliert, der als Zugriffstaste, die entspricht einem `parallel_for_each` aufrufen.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Ruft ein Flag, das angibt, ob die Daten von einem Aggregat von vielen Symbolen gehört.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Ruft ein Flag, das angibt, ob die Symboldatei C-Typen enthält.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Ruft ein Flag, der angibt, ob das Modul aus Common Intermediate Language (CIL) in systemeigenen Code konvertiert wurde.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Ruft ein Flag, der angibt, ob die Elemente eines benutzerdefinierten Datentyps zu einer bestimmten Begrenzung ausgerichtet sind.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Gibt an, ob dieses Symbol hohen Shader Sprache HLSL (Level) Daten darstellt.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Ruft ein Flag, das angibt, ob das Modul kompiliert wurde, mit der [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](/cpp/build/reference/hotpatch-create-hotpatchable-image) Compilerschalter.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Ruft ein Flag, das angibt, ob der verwaltete Kompiliereinheit mit dem Linker LTCG verknüpft wurde.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Gibt an, ob die Matrix wichtigen Zeile ist.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Ruft ein Flag, das angibt, ob der verwaltete Kompiliereinheit eines .netmodule (enthält nur Metadaten) ist ab.|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Gibt an, ob die `this` Zeiger verweist auf einen Datenmember mit mehrfacher Vererbung.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Ruft ein Flag, das angibt, ob die Funktion verfügt über die [naked](/cpp/cpp/naked-cpp) Attribut.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Gibt an, ob die Variable unterwegs optimiert ist.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Gibt an, ob die `this` Zeiger basiert auf einen Symbolwert.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Gibt an, ob dieses Symbol, ein Zeiger auf einen Datenmember ist.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Gibt an, ob dieses Symbol, ein Zeiger auf eine Memberfunktion ist.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Gibt an, ob die Variable einen Wert zurückgegeben wird.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Gibt an, ob das Modul mit der Option/SDL kompiliert wird.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Gibt an, ob die `this` Zeiger verweist auf einen Datenmember mit einfache Vererbung.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Ruft ein Flag, das angibt, ob die Daten in ein Aggregat getrennte Symbole aufgeteilt wurde.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Ruft ein Flag, das angibt, ob eine Funktion oder Thunk Ebene statisch ist.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Ruft ein Flag, das angibt, ob private Symbole aus der Symboldatei entfernt haben.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Gibt an, ob die `this` Zeiger verweist auf einen Datenmember mit virtueller Vererbung.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Ruft die Sprache der Quelle ab.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Ruft die Anzahl der Bytes an Arbeitsspeicher verwendet, die für das Objekt, das durch dieses Symbol dargestellt.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Ruft einen Verweis auf den übergeordneten lexikalischen des Symbols ab.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Ruft den lexikalischen übergeordneten Bezeichner des Symbols ab.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Ruft den Dateinamen der Bibliothek oder Objektdatei-Datei, an der das Objekt geladen wurde.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Gibt die Länge des-Adressbereichs in der lokalen Symbolcache gültig ist.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Gibt den Abschnitt Teil des Start-Adressbereichs in der lokalen Symbolcache gültig ist.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Gibt den Zeitzonenoffset-Teil des Start-Adressbereichs in der lokalen Symbolcache gültig ist.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Gibt den Anfang der Adressbereich aus, in dem die lokalen Symbolcache gültig ist.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Ruft den Typ eines Daten-Symbols ab.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Ruft die untere Grenze des eine FORTRAN Arraydimension ab.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Ruft den Symbol-Bezeichner, der die untere Grenze des eine FORTRAN Arraydimension ab.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Ruft den Typ der Ziel-CPU ab.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Ruft ein Flag an, dass verwalteter Code, der angibt, ob das Symbol auf verweist.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Ruft die Art der Arbeitsspeicher Speicherplatz ab.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Ruft ein Flag, der angibt, ob das Symbol auf der Microsoft Intermediate Language (MSIL) Code verweist.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Ruft den Namen des Symbols ab.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp geschachtelt ist.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Ruft ein Flag, das angibt, ob die Funktion mit gekennzeichnet ist die [Noinline](/cpp/cpp/noinline) Attribut.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Ruft ein Flag, das angibt, ob die Funktion deklariert wurde mit der [Noreturn](/cpp/cpp/noreturn) Attribut.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Ruft ein Flag, das angibt, ob keine Reihenfolge des Stapels im Rahmen des Puffers stapelüberprüfung erzielt werden kann.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Ruft ein Flag, das angibt, ob die Funktion oder die Bezeichnung niemals erreicht wird.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Gibt die Anzahl der Zugriffstaste Zeiger Tags in einer C++ AMP-Stub-Funktion zurück.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Ruft die Anzahl der Modifizierer, die in den ursprünglichen Typ angewendet werden.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Ruft die Anzahl der Register Indizes ab.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Ruft die Anzahl der Zeilen in der Matrix ab.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Ruft die Anzahl der Spalten in der Matrix ab.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Ruft ab, der Name der Objektdatei.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Ruft den Typ des Zeigers Objekt für eine Klassenmethode ab.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Ruft des Symbols `oemId` Wert.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Ruft des Symbols `oemSymbolId` Wert.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Ruft den Offset des Symbolspeicherort ab.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Ruft ein Flag, das angibt, ob die Funktion oder Bezeichnung optimierten Code enthält auch Debuginformationen.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp überladene Operatoren weist ab.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp gepackt ist.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Ruft ab den Plattformtyp aus, für den das Programm oder Kompiliereinheit kompiliert wurde.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Ruft ein Flag ab, der angibt, ob die Funktion reinen wird virtual.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Ruft den Rang eines mehrdimensionalen Arrays FORTRAN ab.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Ruft ein Flag, das angibt, ob ein Typ ein Verweis ist.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Ruft die Register-Kennzeichner des Speicherorts ab.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Ruft die Register-Typ ab.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse (RVA) des Speicherorts ab.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Gibt an, ob die `this` Zeiger gekennzeichnet ist eingeschränkt.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Ruft den Sampler-Slot ab.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp wird, in eine globale lexikalischen Gültigkeitsbereich angezeigt ab.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Ruft den Symbolwert Signatur ab.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Ruft die Größe eines Elements eines benutzerdefinierten Typs ab.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Ruft die Nummer des Steckplatzes des Speicherorts ab.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Ruft den Dateinamen der Quelldatei ab.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Ruft die Quelle und die Zeilennummer der Anzahl, die angeben, in dem ein angegebenen benutzerdefinierten Typs definiert wird.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Ruft die Stride der Matrix oder strided Array ab.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Ruft den Untertyp ab.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Ruft die Sub-Typ-ID.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Ruft den Namen der Datei aus der die Symbole geladen wurden.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Ruft die eindeutige Symbol-ID ab.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Ruft die Klassifizierung der Symbol-Typ ab.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Ruft ab Offset im Abschnitt ein Thunkziel.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Ruft die relative virtuelle Adresse (RVA) eines Ziels Thunk ab.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Ruft den Adressabschnitt eines Ziels Thunk ab.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Ruft ab, die virtuelle Adresse ("VA" ist), der ein Thunkziel.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Ruft die Textur Slot ab.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Ruft den logischen `this` Abwicklung für die Methode.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Ruft den Thunk-Typ, einer Funktion ab.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Ruft den Zeitstempel der zugrunde liegende ausführbare Datei ab.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Ruft das Metadatentoken der eine verwaltete Funktion oder Variable ab.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Ruft einen Verweis auf die Funktionssignatur ab.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Ruft die Typ-ID des Symbols ab.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Ruft ein Array von compilerspezifisch Typwerte für dieses Symbol ab.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Ruft ein Array von Werten compilerspezifisch Bezeichner für dieses Symbol ab.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Ruft den Slot Uav ab.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Ruft die Vielfalt an einen benutzerdefinierten Typ (UDT) ab.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp nicht ausgerichteten ist ab.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Ruft den nicht ergänzten Namen für eine C++ ergänzt, oder die Verknüpfung, den Namen ab.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Erweiterung der `get_undecoratedName` Methode, die den nicht ergänzten Namen basierend auf dem Wert eines Felds Erweiterung abruft.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Ruft die ID des ursprünglichen Typs (unverändert) ab.|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Ruft die obere Grenze einer FORTRAN Arraydimension ab.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Ruft den Symbol-Bezeichner, der die obere Grenze einer FORTRAN Arraydimension ab.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Ruft den Wert einer Konstante.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Ruft ein Flag, das angibt, ob die Funktion virtuell ist ab.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Ruft die virtuelle Adresse ("VA" ist), der den Speicherort ab.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp eine virtuelle Basisklasse ist.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Ruft den Index der virtuellen Basis Verschiebung Tabelle ab.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Ruft den Offset in die virtuelle Funktionstabelle einer virtuellen Funktion ab.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Ruft den Offset von der virtuellen basiszeiger ab.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Ruft den Typ eines Zeigers virtuellen Basistabelle ab.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Ruft die Symbol-Schnittstelle des Typs von der virtuellen Tabelle für einen benutzerdefinierten Typ ab.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Ruft die ID der virtuellen Tabelle Form des Symbols ab.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp flüchtig ist.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, durch den Aufruf einer der folgenden Methoden:  
  
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
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie die lokalen Variablen für eine Funktion an eine angegebene relative virtuelle Adresse angezeigt. Es zeigt auch, wie Symbole verschiedener Typen miteinander verknüpft sind.  
  
> [!NOTE]
>  `CDiaBSTR` ist eine Klasse, umschließt eine `BSTR` und behandelt automatisch die Zeichenfolge freigeben, wenn es sich bei die Instanziierung den Gültigkeitsbereich verlässt.  
  
```C++  
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
  
## <a name="requirements"></a>Anforderungen  
 `Header:` dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compiland](../../debugger/debug-interface-access/compiland.md)