---
title: Codeanalysewarnungen für verwalteten Code nach CheckId
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ba3d5d157cebe48212128a6eeb0312f9f67c2f3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935989"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Codeanalysewarnungen für verwalteten Code nach CheckId

In der folgenden Tabelle werden Codeanalysewarnungen für verwalteten Code nach dem CheckId-Bezeichner der Warnung aufgeführt.

| CheckId | Warnung | Beschreibung |
|---------| - | - |
| CA1000 | [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md) | Wenn ein statischer Member eines generischen Typs aufgerufen wird, muss das Typargument für den Typ angegeben werden. Wenn ein generischer Instanzmember, der keine Unterstützung für Rückschlüsse bietet, aufgerufen wird, muss das Typargument für den Member angegeben werden. In diesen beiden Fällen ist die Syntax zum Angeben des Typarguments unterschiedlich und leicht zu verwechseln. |
| CA1001 | [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Eine Klasse deklariert und implementiert ein Instanzenfeld, das den System.IDisposable-Typ aufweist, IDisposable jedoch nicht implementiert. Eine Klasse, die ein IDisposable-Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte die IDisposable-Schnittstelle implementieren. |
| CA1002 | [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md) | System.Collections.Generic.List < (der \<(T >) >) ist eine generische Auflistung, die für die Leistung und nicht Vererbung entwickelt wurde. Daher enthält List keine virtuellen Member. Stattdessen sollten die generischen Auflistungen, die im Hinblick auf die Vererbung entworfen wurden, verfügbar gemacht werden. |
| CA1003 | [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md) |Ein Typ enthält einen Delegaten, die "void" zurückgibt, deren Signatur enthält zwei Parameter (der erste ist ein Objekt und das zweite ein Typ, der EventArgs zugewiesen werden), und die übergeordnete Assembly ist Microsoft .NET Framework 2.0 ausgerichtet. |
| CA1004 | [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) | Mithilfe eines Rückschlusses wird das Typargument einer generischen Methode nach dem Typ des an die Methode übergebenen Arguments festgelegt, anstatt nach der expliziten Spezifikation des Typarguments. Um den Rückschluss zu aktivieren, muss die Parametersignatur einer generischen Methode einen Parameter einschließen, der vom selben Typ wie der Typparameter für die Methode ist. In diesem Fall muss das Typargument nicht angegeben werden. Wenn für alle Typparameter der Rückschluss verwendet wird, ist die Syntax zum Aufrufen von generischen und nicht generischen Instanzenmethoden identisch. Dies vereinfacht die Verwendung generischer Methoden. |
| CA1005 | [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md) | Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Es ist in der Regel mit einem Typparameter, z. B. List offensichtlich\<T >, und in bestimmten Fällen, die zwei Typparameter, z. B. in Dictionary\<TKey, TValue >. Mehr als zwei Typparameter hingegen bereiten den meisten Benutzern Schwierigkeiten. |
| CA1006 | [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md) | Ein geschachteltes Typargument ist ein Typargument, das auch ein generischer Typ ist. Um einen Member aufzurufen, dessen Signatur ein geschachteltes Typargument enthält, muss der Benutzer einen generischen Typ instanziieren und diesen an den Konstruktor eines zweiten generischen Typs übergeben. Die erforderliche Prozedur und die Syntax sind komplex, und diese Vorgehensweise sollte daher vermieden werden. |
| CA1007 |[CA1007: NACH MÖGLICHKEIT Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md) | Eine extern sichtbare Methode enthält einen Verweisparameter vom Typ System.Object. Bei Verwendung einer generischen Methode können alle Typen mit gewissen Einschränkungen an die Methode übergeben werden, ohne dass der Typ zuvor in den Typ des Verweisparameters umgewandelt werden muss. |
| CA1008 | [CA1008: -Enumerationen sollten NULL-Wert aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md) | Der Standardwert einer nicht initialisierten Enumeration ist ebenso wie der anderer Werttypen 0 (null). Eine Enumeration ohne das Flags-Attribut sollte einen Member mit dem Wert 0 (null) definieren, damit der Standardwert ein gültiger Wert der Enumeration ist. Wenn eine Enumeration, auf die FlagsAttribute angewendet wird, einen Member mit dem Wert 0 (null) definiert, sollte dieser den Namen "None" haben, um anzugeben, dass in der Enumeration keine Werte festgelegt wurden. |
| CA1009 | [CA1009: Ereignishandler korrekt deklarieren](../code-quality/ca1009-declare-event-handlers-correctly.md) | Ereignishandlermethoden nehmen zwei Parameter an. Der erste ist vom Typ System.Object und hat den Namen "sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Typ System.EventArgs und hat den Namen "e". Dies sind die Daten, die dem Ereignis zugeordnet sind. Ereignishandlermethoden geben normalerweise keinen Wert zurück. In der Programmiersprache C# wird dies mit dem void-Rückgabetyp angegeben. |
| CA1010 | [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md) | Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Anschließend kann die Auflistung zum Auffüllen generischer Auflistungstypen verwendet werden. |
| CA1011 |[CA1011: Betrachten Sie Basistypen als Parameter übergeben.](../code-quality/ca1011-consider-passing-base-types-as-parameters.md) | Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden. Wenn die vom abgeleiteten Parametertyp bereitgestellte zusätzliche Funktionalität nicht erforderlich ist, lässt die Verwendung des Basistyps eine allgemeinere Nutzung der Methode zu. |
| CA1012 | [CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen.](../code-quality/ca1012-abstract-types-should-not-have-constructors.md) | Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen und Sie keine Instanzen eines abstrakten Datentyps erstellen können, ist ein abstrakter Datentyp mit einem öffentlichen Konstruktor fehlerhaft konzipiert. |
| CA1013 | [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md) | Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren. |
| CA1014 | [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md) | In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Um guten Entwurfsprinzipien gerecht zu werden, muss bei allen Assemblys die CLS-Kompatibilität mit <xref:System.CLSCompliantAttribute> explizit angegeben werden. Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel. |
| CA1016 | [CA1016: Assemblys mit AssemblyVersionAttribute markieren](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md) | .NET Framework verwendet die Versionsnummer, um eine Assembly eindeutig zu identifizieren, und klicken Sie zum Binden an Datentypen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden. |
| CA1017 | [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md) |Das ComVisibleAttribute-Attribut bestimmt, wie COM-Clients auf verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. Die COM-Sichtbarkeit kann für die gesamte Assembly festgelegt und anschließend für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut fehlt, ist der Inhalt der Assembly für COM-Clients sichtbar. |
| CA1018 | [CA1018: Attribute mit AttributeUsageAttribute markieren](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md) | Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von AttributeUsageAttribute, um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. |
| CA1019 | [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) | Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen. |
| CA1020 | [CA1020: Namespaces mit wenigen Typen vermeiden](../code-quality/ca1020-avoid-namespaces-with-few-types.md) | Stellen Sie sicher, dass jeder der Namespaces logisch organisiert ist und dass es einen zulässigen Grund dafür gibt, Typen in einen wenig gefüllten Namespace einzufügen. |
| CA1021 | [CA1021: Out-Parameter vermeiden](../code-quality/ca1021-avoid-out-parameters.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen dem out-Parameter und dem ref-Parametern oft unklar. |
| CA1023 | [CA1023: Indexer sollten nicht mehrdimensional sein.](../code-quality/ca1023-indexers-should-not-be-multidimensional.md) | Indexer, d. h. indizierte Eigenschaften, sollten einen einzelnen Index verwenden. Wegen mehrdimensionaler Indexer kann die Verwendbarkeit der Bibliothek deutlich abnehmen. |
| CA1024 | [CA1024: NACH MÖGLICHKEIT Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md) | Eine öffentliche oder geschützte Methode hat einen Namen, der mit "Get" beginnt. Sie nimmt keine Parameter an und gibt einen Wert zurück, bei dem es sich nicht um ein Array handelt. Die Methode ist möglicherweise als Eigenschaft geeignet. |
| CA1025 | [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md) | Verwenden Sie ein Parameterarray statt sich wiederholender Argumente, wenn die genaue Anzahl der Argumente nicht bekannt ist und diese Argumente vom gleichen Typ sind oder als gleicher Typ übergeben werden können. |
| CA1026 | [CA1026: Standardparameter sollten nicht verwendet werden](../code-quality/ca1026-default-parameters-should-not-be-used.md) | Methoden, die Standardparameter verwenden, sind nach der CLS zulässig. Die CLS lässt jedoch zu, dass die Werte, die diesen Parametern zugewiesen sind, von Compilern ignoriert werden. Damit das gewünschte Verhalten in verschiedenen Programmiersprachen erhalten bleibt, müssen Methoden, die Standardparameter verwenden, durch Methodenüberladungen ersetzt werden, von denen die Standardparameter bereitgestellt werden. |
| CA1027 |[CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Wenden Sie FlagsAttribute auf eine Enumeration an, wenn deren benannte Konstanten sinnvoll kombiniert werden können. |
| CA1028 | [CA1028: Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Standardmäßig wird zum Speichern des konstanten Werts der System.Int32-Datentyp verwendet. Sie können diesen zugrunde liegenden Typ zwar ändern, in den meisten Szenarien ist dies jedoch weder notwendig noch empfehlenswert. |
| CA1030 | [CA1030: NACH MÖGLICHKEIT Verwenden Sie Ereignisse](../code-quality/ca1030-use-events-where-appropriate.md) |Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Wenn eine Methode auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen. |
| CA1031 | [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md) | Allgemeine Ausnahmen sollten nicht abgefangen werden. Fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme in der letzten Anweisung des catch-Blocks erneut aus. |
| CA1032 |[CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md) | Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. |
| CA1033 | [CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md) | Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an. |
| CA1034 | [CA1034: Geschachtelte Typen sollten nicht sichtbar sein.](../code-quality/ca1034-nested-types-should-not-be-visible.md) | Ein geschachtelter Typ ist ein Typ, der innerhalb des Gültigkeitsbereichs eines anderen Typs deklariert ist. Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails der enthaltenden Typen. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein. |
| CA1035 | [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md) | Nach dieser Regel müssen ICollection-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den Object-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. Diese Regel geht davon aus, dass der Typ, der ICollection implementiert, diese Implementierung zur Verwaltung einer Auflistung von Instanzen eines Typs vornimmt, der stärker ist als Object. |
| CA1036 | [CA1036: Methoden bei vergleichbaren Typen überschreiben](../code-quality/ca1036-override-methods-on-comparable-types.md) |Ein öffentlicher oder geschützter Typ implementiert die System.IComparable-Schnittstelle. Er überschreibt Object.Equals nicht und überlädt auch nicht den sprachspezifischen Operator für gleich, ungleich, kleiner als und größer als. |
| CA1038 | [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md) | Nach dieser Regel müssen IEnumerator-Implementierungen für die Current-Eigenschaft auch eine Version mit starker Typisierung angeben, damit die Benutzer den Rückgabewert nicht in den starken Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. |
| CA1039 | [CA1039: Listen sind stark typisiert.](../code-quality/ca1039-lists-are-strongly-typed.md) | Nach dieser Regel müssen IList-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den System.Object-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. |
| CA1040 |[CA1040: Leere Schnittstellen vermeiden](../code-quality/ca1040-avoid-empty-interfaces.md) | Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Daher definiert sie keinen Vertrag, der implementiert werden kann. |
| CA1041 | [CA1041: ObsoleteAttribute-Meldung](../code-quality/ca1041-provide-obsoleteattribute-message.md) | Ein Typ oder Member wird mit einem System.ObsoleteAttribute-Attribut markiert, dessen ObsoleteAttribute.Message-Eigenschaft nicht angegeben wurde. Wenn ein mit ObsoleteAttribute markierter Typ oder Member kompiliert wird, wird die Message-Eigenschaft des Attributs angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. |
| CA1043 | [CA1043: GANZZAHLIGES Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md) | Indexer (d. h. indizierte Eigenschaften) sollten ganzzahlige Typen oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. R. zum Indizieren von Datenstrukturen verwendet und erweitern den Einsatzbereich der Bibliothek. Die Verwendung des Object-Typs sollte auf die Fälle beschränkt werden, in denen der spezielle integrale oder Zeichenfolgentyp zur Entwurfszeit nicht angegeben werden kann. |
| CA1044 | [CA1044: Eigenschaften sollten nicht lesegeschützt sein.](../code-quality/ca1044-properties-should-not-be-write-only.md) | Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Wenn ein Benutzer einen Wert festlegen kann, bietet es keinerlei Sicherheitsvorteile, das Lesen und Anzeigen des Werts durch den Benutzer zu sperren. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird. |
| CA1045 |[CA1045: Typen nicht als Verweis übergeben](../code-quality/ca1045-do-not-pass-types-by-reference.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Entwickler von Bibliotheken für eine breite Zielgruppe sollten nicht davon ausgehen, dass die Benutzer den out-Parameter oder den ref-Parameter richtig verwenden können. |
| CA1046 | [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md) | Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen. |
| CA1047 |[CA1047: Geschützte Member in versiegelten Typen nicht deklarieren](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md) | Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können. Per Definition kann von versiegelten Typen nicht geerbt werden. Dies bedeutet, dass geschützte Methoden für versiegelte Typen nicht aufgerufen werden können. |
| CA1048 | [CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md) | Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Per Definition kann ein versiegelter Typ nicht geerbt werden. Dadurch wird eine virtuelle Methode für einen versiegelten Typ bedeutungslos. |
| CA1049 | [CA1049: Typen, die systemeigene Ressourcen besitzen müssen gelöscht werden können.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md) | Typen, die nicht verwaltete Ressourcen zuordnen, müssen IDisposable implementieren, damit Aufrufer diese Ressourcen bei Bedarf freigeben und die Lebensdauer der Objekte verkürzen können, die diese Ressourcen verwenden. |
| CA1050 | [CA1050: Typen in Namespaces deklarieren](../code-quality/ca1050-declare-types-in-namespaces.md) | Typen werden in Namespaces deklariert, um Namenskonflikte zu verhindern und um verwandte Typen in einer Objekthierarchie zu organisieren. |
| CA1051 | [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) | Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder sollten privat oder intern sein und durch die Verwendung von Eigenschaften verfügbar gemacht werden. |
| CA1052 | [CA1052: Statische Haltertypen sollten versiegelt sein](../code-quality/ca1052-static-holder-types-should-be-sealed.md) | Ein öffentlicher oder geschützter Typ enthält nur statische Member und wird nicht mit dem sealed (C#-Referenz)-Modifizierer (NotInheritable) deklariert. Ein Typ, der nicht geerbt werden soll, sollte mit dem sealed-Modifizierer markiert werden, um seine Verwendung als Basistyp zu verhindern. |
| CA1053 |[CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md) | Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor. Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Die Zeichenfolgenüberladung sollte die URI-Überladung aus Sicherheitsgründen mit dem Zeichenfolgenargument aufrufen. |
| CA1054 | [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md) | Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, sollte eine entsprechende Überladung angegeben werden, die eine Instanz der URI-Klasse annimmt, die diese Dienste auf sichere Weise bereitstellt. |
| CA1055 | [CA1055: URI-Rückgabewerte sollten keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md) | Diese Regel geht davon aus, dass die Methode einen URI zurückgibt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1056 | [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md) | Diese Regel geht davon aus, dass die Eigenschaft einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1057 | [CA1057: URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md) | Ein Typ deklariert Methodenüberladungen, die sich nur durch die Ersetzung eines Zeichenfolgenparameters mit einem System.Uri-Parameter unterscheiden. Die Überladung, die den Zeichenfolgenparameter akzeptiert, ruft nicht die Überladung auf, die den URI-Parameter akzeptiert. |
| CA1058 | [CA1058: Typen sollten bestimmte Basistypen nicht erweitern.](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Verwenden Sie eine der Alternativen. |
| CA1059 |[CA1059: Member sollten bestimmte konkreten Typen nicht verfügbar machen](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md) | Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann. Damit der Member universell verwendet werden kann, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle. |
| CA1060 | [CA1060: Verschieben von P/Invokes in NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md) | Plattformaufrufmethoden, beispielsweise Methoden, die mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut gekennzeichnet sind, oder Methoden, die in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mithilfe des Declare-Schlüsselworts definiert wurden, greifen auf nicht verwalteten Code zu. Diese Methoden sollten der Klasse NativeMethods, SafeNativeMethods oder UnsafeNativeMethods angehören. |
| CA1061 |[CA1061: Basisklassenmethoden nicht ausblenden](../code-quality/ca1061-do-not-hide-base-class-methods.md) | Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ verdeckt, wenn die Parametersignatur der abgeleiteten Methode sich nur hinsichtlich der Typen unterscheidet, die schwächer abgeleitet sind als die entsprechenden Typen in der Parametersignatur der Basismethode. |
| CA1062 | [CA1062: Argumente von öffentlichen Methoden validieren](../code-quality/ca1062-validate-arguments-of-public-methods.md) | Alle an extern sichtbare Methoden übergebenen Verweisargumente sollten auf NULL überprüft werden. |
| CA1063 | [CA1063: IDisposable korrekt implementieren](../code-quality/ca1063-implement-idisposable-correctly.md) | Alle IDisposable-Typen müssen das Dispose-Muster korrekt implementieren. |
| CA1064 | [CA1064: Ausnahmen sollten öffentlich sein.](../code-quality/ca1064-exceptions-should-be-public.md) | Eine interne Ausnahme ist nur innerhalb ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme von geerbt wird <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>, der externe Code müssen nicht über genügend Informationen zur Vorgehensweise mit der Ausnahme. |
| CA1065 | [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus. |
| CA1300 | [CA1300: MessageBoxOptions angeben](../code-quality/ca1300-specify-messageboxoptions.md) | Wenn in Kulturen, in denen von rechts nach links gelesen wird, ein Meldungsfeld richtig angezeigt werden soll, müssen der RightAlign-Member und der RtlReading-Member der MessageBoxOptions-Enumeration an die Show-Methode übergeben werden. |
| CA1301 | [CA1301: Doppelte Zugriffstasten vermeiden](../code-quality/ca1301-avoid-duplicate-accelerators.md) | Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent. |
| CA1302 | [CA1302: Keine hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md) | Die System.Environment.SpecialFolder-Enumeration enthält Member, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können sich von Betriebssystem zu Betriebssystem unterscheiden. Der Benutzer kann einige Speicherorte ändern, und die Speicherorte sind lokalisiert. Die Environment.GetFolderPath-Methode gibt die der Environment.SpecialFolder-Enumeration zugeordneten Speicherorte zurück, die lokalisiert und für den derzeit ausgeführten Computer geeignet sind. |
| CA1303 | [CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md) | Eine extern sichtbare Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder-Methode in der .NET Framework-Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein. |
| CA1304 | [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md) | Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen System.Globalization.CultureInfo-Parameter akzeptiert. Die Methode oder der Konstruktor ruft nicht die Überladung auf, die den CultureInfo-Parameter akzeptiert. Wenn ein CultureInfo-Objekt oder ein System.IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1305 | [CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md) | Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen System.IFormatProvider-Parameter akzeptieren; die Methode oder der Konstruktor ruft die Überladung nicht auf, die den IFormatProvider-Parameter akzeptiert. Wenn ein System.Globalization.CultureInfo-Objekt oder ein IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1306 | [CA1306: Set-Gebietsschema für Datentypen](../code-quality/ca1306-set-locale-for-data-types.md) | Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten wie die für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Wenn Sie eine DataTable oder ein DataSet erstellen, sollten Sie das Gebietsschema explizit festlegen. |
| CA1307 | [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md) | Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein StringComparison-Parameter festgelegt wird. |
| CA1308 |[CA1308: Zeichenfolgen in Großbuchstaben normalisieren](../code-quality/ca1308-normalize-strings-to-uppercase.md) | Zeichenfolgen sollten in Großschreibung normalisiert werden. Für eine kleine Gruppe von Zeichen wird bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt. |
| CA1309 | [CA1309: Ordinal-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md) | Durch einen nicht linguistischen Zeichenfolgenvergleich wird der StringComparison-Parameter nicht auf Ordinal und nicht auf OrdinalIgnoreCase festgelegt. Wenn der Parameter explizit auf StringComparison.Ordinal oder StringComparison.OrdinalIgnoreCase festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert. |
| CA1400 | [CA1400: P/Invoke-Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) |Eine öffentliche oder geschützte Methode wird mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut markiert. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. |
| CA1401 | [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Eine öffentliche oder geschützte Methode in einem öffentlichen Typ enthält das System.Runtime.InteropServices.DllImportAttribute-Attribut (in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] auch durch das Declare-Schlüsselwort implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| CA1402 |[CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem dem Namen ein Unterstrich (_) und eine ganze Zahl angefügt werden, die der Reihenfolge der Deklaration der Überladung entspricht. |
| CA1403 | [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | Ein für COM sichtbarer Werttyp wird mit dem auf LayoutKind.Auto festgelegten System.Runtime.InteropServices.StructLayoutAttribute-Attribut markiert. Das Layout dieser Typen kann zwischen Versionen von .NET Framework ändern, die COM-Clients unterbrochen wird, die ein bestimmtes Layout erwarten. |
| CA1404 | [CA1404: GetLastError unmittelbar nach P/Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Wird aufgerufen, GetLastWin32Error-Methode oder einer entsprechenden [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError-Funktion, und der unmittelbar vorherige Aufruf ist nicht für ein Betriebssystem invoke-Methode. |
| CA1405 | [CA1405: COM sichtbare Basistypen sollten für COM sichtbar sein](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | Ein für COM sichtbarer Typ wird von einem Typ abgeleitet, der nicht für COM sichtbar ist. |
| CA1406 |[CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen. |
| CA1407 |[CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM unterstützt keine statischen Methoden. |
| CA1408 | [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. Standardmäßig wird eine auf Dispatch beschränkte Schnittstelle verwendet, wenn das ClassInterfaceAttribute-Attribut nicht angegeben wird. |
| CA1409 | [CA1409: Für COM sichtbare Typen müssen erstellt werden können.](../code-quality/ca1409-com-visible-types-should-be-creatable.md) |Ein Verweistyp, der speziell als für COM sichtbar gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, jedoch keinen öffentlichen (parameterlosen) Standardkonstruktor. Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht von COM-Clients erstellt werden. |
| CA1410 | [CA1410: COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Ein Typ deklariert eine mit dem System.Runtime.InteropServices.ComRegisterFunctionAttribute-Attribut markierte Methode, aber keine mit dem System.Runtime.InteropServices.ComUnregisterFunctionAttribute-Attribut markierte Methode oder umgekehrt. |
| CA1411 | [CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | Eine mit dem System.Runtime.InteropServices.ComRegisterFunctionAttribute-Attribut oder dem System.Runtime.InteropServices.ComUnregisterFunctionAttribute-Attribut markierte Methode ist extern sichtbar. |
| CA1412 | [CA1412: ComSource-Schnittstellen als IDispatch markieren](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | Ein Typ ist mit dem System.Runtime.InteropServices.ComSourceInterfacesAttribute-Attribut markiert, und mindestens eine der angegebenen Schnittstellen ist nicht mit dem auf ComInterfaceType.InterfaceIsIDispatch festgelegten System.Runtime.InteropServices.InterfaceTypeAttribute-Attribut markiert. |
| CA1413 | [CA1413: Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt der Felder auf Informationen, die nicht verfügbar gemacht werden sollen oder unbeabsichtigte Auswirkungen auf Design oder Sicherheit haben. |
| CA1414 | [CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Der boolesche Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. |
| CA1415 | [CA1415: P/Invokes korrekt deklarieren](../code-quality/ca1415-declare-p-invokes-correctly.md) | Diese Regel sucht nach Deklarationen für eine Aufrufmethode des Betriebssystems, die [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]-Funktionen mit einem Zeiger auf einen OVERLAPPED-Strukturparameter zum Ziel haben, der zugehörige verwaltete Parameter ist jedoch kein Zeiger auf eine System.Threading.NativeOverlapped-Struktur. |
| CA1500 | [CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen.](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Mit einer Instanzenmethode wird ein Parameter oder eine lokale Variable deklariert, dessen bzw. deren Name mit dem Namen eines Instanzenfelds des deklarierenden Typs übereinstimmt. Dies führt zu Fehlern. |
| CA1501 | [CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md) | Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. |
| CA1502 | [CA1502: Übermäßige Komplexität vermeiden](../code-quality/ca1502-avoid-excessive-complexity.md) | Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird. |
| CA1504 | [CA1504: Irreführende Feldnamen überprüfen](../code-quality/ca1504-review-misleading-field-names.md) | Der Name eines Instanzenfelds beginnt mit "S_", oder der Name eines statischen Felds (Shared in Visual Basic) beginnt mit "M_". |
| CA1505 | [CA1505: Nicht wartbaren Code vermeiden](../code-quality/ca1505-avoid-unmaintainable-code.md) | Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre. |
| CA1506 |[CA1506: Übermäßige Klassenkopplungen vermeiden](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden. |
| CA1600 | [CA1600: Verwenden Sie nicht im Leerlauf Prozesse mit der Priorität](../code-quality/ca1600-do-not-use-idle-process-priority.md) | Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus. |
| CA1601 | [CA1601: Verwenden Sie keine Timer, die Änderungen am Betriebszustand zu verhindern.](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden. |
| CA1700 | [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. |
| CA1701 | [CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md) | Jeder Begriff in der Ressourcenzeichenfolge wird basierend auf der Groß-/Kleinschreibung in einzelne Token unterteilt. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. |
| CA1702 | [CA1702: BEI Bei zusammengesetzten Begriffen sollte beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md) | Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung. |
| CA1703 | [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md) | Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA1704 | [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md) | Der Name eines extern sichtbaren Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA1707 | [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md) | Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft. |
| CA1708 | [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md) | Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen. |
| CA1709 | [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md) | Gemäß der Konvention werden Parameternamen in Kamel-Schreibweise verfasst, für Namespace-, Typ- und Membernamen wird die Pascal-Schreibweise verwendet. |
| CA1710 | [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md) |Die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen weisen stets ein Suffix auf, das mit dem Basistyp oder der Schnittstelle verknüpft ist. |
| CA1711 | [CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md) | Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden. |
| CA1712 | [CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md) | Den Namen von Enumerationsmembern wird der Typname nicht als Präfix vorangestellt, da die Typinformationen von den Entwicklungswerkzeugen bereitgestellt werden sollten. |
| CA1713 | [CA1713: Ereignisse sollten kein Before- oder after-Präfix aufweisen.](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md) | Der Name eines Ereignisses beginnt mit "Before" oder "After". Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben. |
| CA1714 | [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714-flags-enums-should-have-plural-names.md) | Eine öffentliche Enumeration verfügt über das System.FlagsAttribute-Attribut, und der Name endet nicht in der Pluralform ("s"). Die Namen von mit FlagsAttribute markierten Typen stehen im Plural, da das Attribut angibt, dass mehr als ein Wert festgelegt werden kann. |
| CA1715 | [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md) | Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem großen "I". Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit einem großen "T". |
| CA1716 | [CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.](../code-quality/ca1716-identifiers-should-not-match-keywords.md) | Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein. Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind. |
| CA1717 | [CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können. |
| CA1719 | [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md) | Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek. |
| CA1720 |[CA1720: Bezeichner dürfen keine Typnamen enthalten.](../code-quality/ca1720-identifiers-should-not-contain-type-names.md) | Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen. |
| CA1721 | [CA1721: Eigenschaftennamen sollten nicht mit dem Get-Methoden übereinstimmen.](../code-quality/ca1721-property-names-should-not-match-get-methods.md) |Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get"-Methoden und -Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen. |
| CA1722 | [CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md) | Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen. |
| CA1724 | [CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.](../code-quality/ca1724-type-names-should-not-match-namespaces.md) | Typnamen sollten nicht die Namen von Namespaces mit übereinstimmen, die in der .NET Framework-Klassenbibliothek definiert sind. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden. |
| CA1725 | [CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen](../code-quality/ca1725-parameter-names-should-match-base-declaration.md) | Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt. |
| CA1726 | [CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md) | Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Der Name kann auch den Begriff "Flag" oder "Flags" enthalten. |
| CA1800 | [CA1800: Keine unnötigen Umwandlungen](../code-quality/ca1800-do-not-cast-unnecessarily.md) | Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. |
| CA1801 | [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md) | Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. |
| CA1802 |[CA1802: NACH MÖGLICHKEIT Verwenden Sie Literale](../code-quality/ca1802-use-literals-where-appropriate.md) |Ein Feld wird als static und read-only deklariert (Shared und ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) und mit einem Wert initialisiert, der zur Kompilierungszeit berechnet werden kann. Da der Wert, der dem verwendeten Feld zugewiesen wird zum Zeitpunkt der Kompilierung zu berechnendes ist, ändern Sie die Deklaration in ein Const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird. |
| CA1804 | [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md) | Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung. |
| CA1806 | [CA1806: Methodenergebnisse nicht ignorieren](../code-quality/ca1806-do-not-ignore-method-results.md) | Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM-Methode oder P/Invoke-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird. |
| CA1809 |[CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md) | Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als Registrierung des Werts bezeichnet. Um die Wahrscheinlichkeit zu erhöhen, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64. |
| CA1810 | [CA1810: Statische Felder von Verweistypen Inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. |
| CA1811 | [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md) | Zu einem privaten oder internen Member (auf Assemblyebene) gibt es in der Assembly keine Aufrufer. Er wird nicht durch die Common Language Runtime und nicht durch einen Delegaten aufgerufen. |
| CA1812 | [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt. |
| CA1813 | [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md) | Die .NET Framework-Klassenbibliothek stellt Methoden zum Abrufen von benutzerdefinierten Attributen bereit. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Durch Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert. |
| CA1814 | [CA1814: Verzweigte Arrays mehrdimensionalen bevorzugen](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird. |
| CA1815 | [CA1815: Außer Kraft setzen equals und Gleichheitsoperator für Werttypen](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Bei Werttypen wird die Reflection-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. |
| CA1816 | [CA1816: Rufen Sie GC. SuppressFinalize ordnungsgemäß](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Eine Methode, die eine Implementierung von Dispose bildet, ruft nicht GC auf. SuppressFinalize; oder eine Methode, die eine Implementierung von Dispose nicht ist, ruft GC. SuppressFinalize; oder eine Methode aufruft, GC. SuppressFinalize aus und übergibt ein anderes Element als dieses (Me in Visual Basic). |
| CA1819 | [CA1819: Eigenschaften sollten keine Arrays zurückgeben.](../code-quality/ca1819-properties-should-not-return-arrays.md) | Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. |
| CA1820 | [CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | Der Vergleich von Zeichenfolgen mit der String.Length-Eigenschaft oder der String.IsNullOrEmpty-Methode führt erheblich schneller zu Ergebnissen als das Verwenden von Equals. |
| CA1821 | [CA1821: Leere Finalizer entfernen](../code-quality/ca1821-remove-empty-finalizers.md) | Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Ein leerer Finalizer verursacht zusätzlichen Mehraufwand ohne Nutzen. |
| CA1822 |[CA1822: Member als statisch markieren](../code-quality/ca1822-mark-members-as-static.md) | Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen. |
| CA1823 | [CA1823: Nicht verwendete private Felder vermeiden](../code-quality/ca1823-avoid-unused-private-fields.md) | Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt. |
| CA1824 |[CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Mit dem NeutralResourcesLanguage-Attribut wird dem ResourceManager die Sprache mitgeteilt, in der die Ressourcen einer neutralen Kultur für eine Assembly angezeigt wurden. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern. |
| CA1900 | [CA1900: Werttypfelder sollten portabel sein.](../code-quality/ca1900-value-type-fields-should-be-portable.md) | Anhand dieser Regel wird überprüft, ob die mit explizitem Layout deklarierten Strukturen korrekt ausgerichtet werden, wenn sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden. |
| CA1901 | [CA1901: Deklarationen von P/Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md) | Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P/Invoke-Deklaration aus und überprüft die zugehörige Größe der Parameter beim Marshallen an nicht verwalteten Code unter einem 32-Bit- oder 64-Bit-Betriebssystem. |
| CA1903 | [CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903-use-only-api-from-targeted-framework.md) | Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist. |
| CA2000 | [CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md) | Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden. |
| CA2001 | [CA2001: Keine problematischen Methoden aufrufen](../code-quality/ca2001-avoid-calling-problematic-methods.md) | Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf. |
| CA2002 |[CA2002: Klicken Sie auf Objekten mit schwacher Identität nicht sperren](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md) |Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt. |
| CA2003 |[CA2003: Fibers nicht als Threads behandeln](../code-quality/ca2003-do-not-treat-fibers-as-threads.md) | Ein verwalteter Thread wird als [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]-Thread behandelt. |
| CA2004 | [CA2004: Entfernen Sie Aufrufe von GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md) | Wenn Sie zur Verwendung von SafeHandle wechseln, entfernen Sie alle Aufrufe an GC.KeepAlive (Objekt). In diesem Fall sollten Klassen GC.KeepAlive nicht aufrufen müssen. Dabei wird davon ausgegangen, dass sie keinen Finalizer verwenden, sondern sich auf SafeHandle verlassen, um das Betriebssystemhandle zu beenden. |
| CA2006 | [CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md) | Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist. |
| CA2100 | [CA2100: Überprüfen Sie die SQL-Abfragen für Sicherheitsrisiken](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md) | Eine Methode legt die System.Data.IDbCommand.CommandText-Eigenschaft mithilfe einer Zeichenfolge fest, die aus einem Zeichenfolgenargument für die Methode erstellt wird. Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. |
| CA2101 |[CA2101: Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Ein Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling der Zeichenfolge durch. Auf diese Weise kann potenziell eine Sicherheitslücke verursacht werden. |
| CA2102 | [CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md) | Ein Member in einer Assembly, die nicht mit dem RuntimeCompatibilityAttribute bzw. mit RuntimeCompatibility(WrapNonExceptionThrows = false) gekennzeichnet ist, enthält einen Catch-Block zur Behandlung von System.Exception und keinen unmittelbar folgenden allgemeinen Catch-Block. |
| CA2103 | [CA2103: Imperative Sicherheit überprüfen](../code-quality/ca2103-review-imperative-security.md) |Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist. Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. |
| CA2104 |[CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md) | Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt. Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. |
| CA2105 | [CA2105: Arrayfelder dürfen nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md) |Wenn Sie den schreibgeschützten Modifizierer (ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) auf ein Feld mit einem Array anwenden, kann das Feld nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. |
| CA2106 | [CA2106: Sichere Bestätigungen](../code-quality/ca2106-secure-asserts.md) | Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt. Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. |
| CA2107 | [CA2107: VERWENDUNG Deny und PermitOnly überprüfen](../code-quality/ca2107-review-deny-and-permit-only-usage.md) |Die PermitOnly-Methode und die CodeAccessPermission.Deny-Sicherheitsaktionen sollten nur von Personen mit Kenntnissen der .NET Framework-Sicherheit verwendet werden. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden. |
| CA2108 | [CA2108: Deklarative Sicherheit auf Werttypen überprüfen](../code-quality/ca2108-review-declarative-security-on-value-types.md) | Ein öffentlicher oder geschützter Werttyp wird durch Datenzugriff oder Linkaufrufe gesichert. |
| CA2109 | [CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md) | Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt. Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist. |
| CA2111 |[CA2111: Zeiger sollten nicht sichtbar sein.](../code-quality/ca2111-pointers-should-not-be-visible.md) | Ein Zeiger ist nicht privat, intern oder schreibgeschützt. Bösartiger Code kann den Wert des Zeigers ändern und damit potenziell Zugriffe auf beliebige Speicherbereiche ermöglichen oder Anwendungs- bzw. Systemfehler verursachen. |
| CA2112 | [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md) | Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird durch Linkaufrufe gesichert. Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen. |
| CA2114 | [CA2114: Methodensicherheit sollte Superset des Typs sein.](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md) | Eine Methode sollte bei der gleichen Aktion nicht sowohl auf einer Methodenebene als auch auf einer Typebene deklarative Sicherheit aufweisen. |
| CA2115 | [CA2115: Rufen Sie GC. KeepAlive beim Verwenden systemeigener Ressourcen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md) | Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird. |
| CA2116 | [CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md) |Wenn eine voll vertrauenswürdige Assembly über das APTCA-Attribut (AllowPartiallyTrustedCallersAttribute) verfügt und die Assembly Code in einer anderen Assembly ausführt, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden. |
| CA2117 | [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md) | Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein in der Assembly enthaltener Typ von einem Typ erbt, der keine nicht voll vertrauenswürdigen Aufrufer zulässt, dann können Sicherheitslücken entstehen, die sich für Angriffe ausnutzen lassen. |
| CA2118 | [CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) |SuppressUnmanagedCodeSecurityAttribute ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code ausführen, der COM-Interop oder Betriebssystemaufrufe verwendet. Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. |
| CA2119 | [CA2119: Versiegeln Sie Methoden, private Schnittstellen erfüllen](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md) | Ein vererbbarer öffentlicher Typ stellt eine überschreibbare Methodenimplementierung einer internen Schnittstelle (Friend in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) bereit. Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird. |
| CA2120 | [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md) | Dieser Typ verfügt über einen Konstruktor, der ein System.Runtime.Serialization.SerializationInfo-Objekt und ein System.Runtime.Serialization.StreamingContext-Objekt (die Signatur des Serialisierungskonstruktors) akzeptiert. Dieser Konstruktor ist nicht durch eine Sicherheitsüberprüfung gesichert. Dagegen ist mindestens einer der normalen Konstruktoren des Typs gesichert. |
| CA2121 | [CA2121: Statische Konstruktoren sollten privat sein.](../code-quality/ca2121-static-constructors-should-be-private.md) | Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird. Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist. Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen. |
| CA2122 | [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md) | Ein öffentlicher oder geschützter Member enthält Linkaufrufe und wird von einem Member aufgerufen, der keine Sicherheitsüberprüfungen ausführt. Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. |
| CA2123 | [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md) | Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Bei einem Verstoß gegen diese Regel kann ein böswilliger Aufrufer den Linkaufruf einfach durch Aufruf der ungesicherten Methode umgehen. |
| CA2124 | [CA2124: Anfällige finally-Klauseln mit äußerem try](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md) | Eine öffentliche oder geschützte Methode enthält einen try/finally-Block. Durch den finally-Block, der nicht wiederum in einen finally-Block eingeschlossen ist, wird der Sicherheitszustand zurückgesetzt. |
| CA2126 | [CA2126: Typlinkaufrufe erfordern vererbungsanforderungen](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md) | Ein öffentlicher unversiegelter Typ wird durch einen Linkaufruf geschützt und verfügt über eine überschreibbare Methode. Weder der Typ noch die Methode wird mit einer Vererbungsanforderung geschützt. |
| CA2127 | [CA2136: Member dürfen keine in Konflikt stehenden transparenzanmerkungen aufweisen.](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Relevanter Code kann nicht in einer 100 % transparenten Assembly auftreten. Diese Regel analysiert die 100 % transparente Assemblys für alle SecurityCritical-Anmerkungen auf den Typ-, Feld- und Methodenebene. |
| CA2128 |[CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden Assert-Vorgänge](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | Diese Regel analysiert alle Methoden und Typen in einer Assembly, die entweder 100 Prozent transparenten oder eine gemischte transparent/kritisch ist, und kennzeichnet alle deklarativen oder imperativen Verwendungen von Assert gekennzeichnet. |
| CA2129 | [CA2140: Transparenter Code muss nicht auf sicherheitskritische Elemente verweisen.](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Mit SecurityTransparentAttribute markierte Methoden rufen nicht öffentliche Member auf, die als SecurityCritical markiert sind. Diese Regel analysiert alle Methoden und Typen in einer Assembly, die gemischt transparent/kritisch ist, und kennzeichnet alle Aufrufe aus transparentem Code an nicht öffentlichen kritischen Code, der nicht als SecurityTreatAsSafe gekennzeichnet ist. |
| CA2130 | [CA2130: Sicherheitskritische Konstanten sollten transparent sein.](../code-quality/ca2130-security-critical-constants-should-be-transparent.md) | Transparenzerzwingung wird nicht für konstante Werte erzwungen, da Compiler konstante Werte inline verwenden, damit zur Laufzeit keine Suche erforderlich ist. Konstante Felder sollten sicherheitstransparent sein, damit Codebearbeiter nicht davon ausgehen, dass dieser transparente Code nicht auf die Konstante zugreifen kann. |
| CA2131 | [CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md) | Ein Typ ist an Typäquivalenz beteiligt, und der Typ selbst oder ein Member oder Feld des Typs wird mit dem SecurityCriticalAttribute-Attribut markiert. Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an Typäquivalenz beteiligt sind. Wenn die CLR einen derartigen Typ erkennt, wird dieser nicht zur Laufzeit mit einem TypeLoadException-Objekt geladen. In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren, statt die Typäquivalenz von tlbimp und den Compilern ausführen zu lassen. |
| CA2132 | [CA2132: Standardkonstruktoren müssen mindestens genauso kritisch sein wie die Standardkonstruktoren des Basistyps sein.](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md) |Typen und Member mit dem SecurityCriticalAttribute können nicht vom Silverlight-Anwendungscode verwendet werden. Sicherheitsrelevante Typen und Member können nur von vertrauenswürdigem Code in der .NET Framework for Silverlight-Klassenbibliothek verwendet werden. Da eine öffentliche oder geschützte Konstruktion in einer abgeleiteten Klasse mindestens die gleiche Transparenz aufweisen muss wie die zugehörige Basisklasse, können Klassen in einer Anwendung nicht von Klassen abgeleitet werden, die als SecurityCritical markiert sind. |
| CA2133 | [CA2133: Delegaten müssen an Methoden mit konsistenter Transparenz gebunden.](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md) | Diese Warnung wird für Methoden ausgelöst, die einen mit dem SecurityCriticalAttribute markierten Delegaten an eine Methode binden, die transparent oder mit dem SecuritySafeCriticalAttribute markiert ist. Die Warnung wird auch bei einer Methode ausgelöst, die einen transparenten oder sicherheitsrelevanten Delegaten an eine wichtige Methode bindet ist. |
| CA2134 | [CA2134: Methoden müssen beim Überschreiben von Basismethoden konsistente Transparenz wahren](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md) |Diese Regel wird ausgelöst, wenn eine mit dem SecurityCriticalAttribute markierte Methode eine Methode überschreibt, die transparent oder mit dem SecuritySafeCriticalAttribute markiert ist. Die Regel wird auch ausgelöst, wenn eine transparente oder mit dem SecuritySafeCriticalAttribute markierte Methode eine Methode überschreibt, die mit dem SecurityCriticalAttribute markiert ist. Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird. |
| CA2135 | [CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md) | LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Markieren Sie, statt LinkDemands zur Erzwingung von Sicherheit zur JIT-Kompilierungszeit zu erzwingen, die Methoden, Typen und Felder mit dem SecurityCriticalAttribute-Attribut. |
| CA2136 | [CA2136: Member dürfen keine in Konflikt stehenden transparenzanmerkungen aufweisen.](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen. Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind. Eine Klasse, die mit dem SecurityCriticalAttribute-Attribut markiert ist, kann z. B. keine Methode enthalten sein, die mit dem SecuritySafeCriticalAttribute-Attribut markiert ist. |
| CA2137 | [CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md) | Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück. Diese Regel wird bei Versuchen von sicherheitstransparentem Code ausgelöst, nicht überprüfbare MISL (Microsoft Intermediate Language) auszuführen. Die Regel enthält jedoch kein vollständiges IL-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL-Überprüfung abzufangen. |
| CA2138 | [CA2138: Transparente Methoden dürfen nicht Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md) | Eine sicherheitstransparente Methode ruft eine Methode auf, die mit dem SuppressUnmanagedCodeSecurityAttribute-Attribut markiert ist. |
| CA2139 | [CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md) | Diese Regel wird von jeder Methode ausgelöst, die transparent ist und versucht, eine prozessdestabilisierende Ausnahme mit dem HandleProcessCorruptedStateExceptionsAttribute-Attribut zu behandeln. Eine Ausnahme, die einen Prozess beschädigt, entspricht einer Ausnahme der CLR Version 4.0-Ausnahmeklassifizierung wie AccessViolationException. Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. |
| CA2140 | [CA2140: Transparenter Code muss nicht auf sicherheitskritische Elemente verweisen.](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Ein Codeelement, das mit dem SecurityCriticalAttribute-Attribut markiert ist, ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden, wird TypeAccessException, MethodAccessException oder FieldAccessException ausgelöst. |
| CA2141 |[CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Eine sicherheitstransparente Methode ruft eine Methode in einer Assembly auf, die nicht mit dem APTCA markiert ist, oder eine sicherheitstransparente Methode erfüllt einen LinkDemand für einen Typ oder eine Methode. |
| CA2142 | [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md) | Diese Regel wird für transparente Methoden ausgelöst, die für den Zugriff LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. |
| CA2143 | [CA2143: Transparente Methoden dürfen keine sicherheitsanforderungen verwenden.](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md) | Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. |
| CA2144 | [CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md) | Der Sicherheitsreview für transparenten Code ist nicht so umfassend wie der Sicherheitsreview für wichtigen Code, da in transparentem Code keine sicherheitsrelevanten Aktionen ausgeführt werden können. Aus einem Bytearray geladene Assemblys könnten in transparentem Code nicht erkannt werden, und dieses Bytearray könnte kritischen oder wichtigeren sicherheitsgeschützten Code enthalten, der überwacht werden muss. |
| CA2145 | [CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity versehen werden](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md) | Methoden, die mit dem SuppressUnmanagedCodeSecurityAttribute-Attribut ergänzt wurden, weisen jeder aufrufenden Methode einen impliziten LinkDemand zu. Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist. Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit dem SecurityCriticalAttribute-Attribut verwendet, macht diese Anforderung für Aufrufer der Methode leichter zu erkennen. |
| CA2146 | [CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen sein.](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md) | Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. |
| CA2147 |[CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden Assert-Vorgänge](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | Als SecurityTransparentAttribute markiertem Code werden keine ausreichenden Berechtigungen für Assertions erteilt. |
| CA2149 | [CA2149: Transparente Methoden dürfen nicht in systemeigenen Code aufrufen.](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md) | Diese Regel wird für jede transparente Methode ausgelöst, die direkt einen Aufruf in nativen Code ausführt (z. B. mit einem P/Invoke-Aufruf). Verstöße gegen diese Regel führen im Transparenzmodell der Ebene 2 zu einer MethodAccessException und im Transparenzmodell der Ebene 1 zu einer vollständigen Anforderung für UnmanagedCode. |
| CA2151 |[CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein.](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md) | Um sicherheitskritische Typen zu verwenden, muss der Code, der auf den Typ verweist, entweder sicherheitskritisch oder sicherungskritisch sein. Dies gilt auch, wenn der Verweis indirekt ist. Daher kann ein sicherheitstransparentes oder sicherungskritisches Feld irreführend sein, denn transparenter Code kann trotzdem nicht auf das Feld zugreifen. |
| CA2200 | [CA2200: Erneut ausführen Sie, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md) | Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren. |
| CA2201 | [CA2201: Keine reservierten Ausnahmetypen auslösen](../code-quality/ca2201-do-not-raise-reserved-exception-types.md) | Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2202 | [CA2202: Objekte nicht mehrmals verwerfen](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md) |Eine Methodenimplementierung enthält Codepfade, die für dasselbe Objekt mehrere Aufrufe von System.IDisposable.Dispose oder einer Entsprechung von Dispose (z. B. einer Close()-Methode für bestimmte Typen) verursachen können. |
| CA2204 | [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md) | Ein Zeichenfolgenliteral in einem Methodentext enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA2205 | [CA2205: Verwenden Sie verwaltete Entsprechungen der Win32-API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md) | Rufen Sie ein Betriebssystem ist definiert, und eine Methode mit der entsprechenden Funktionalität befindet sich in der .NET Framework-Klassenbibliothek. |
| CA2207 | [CA2207: Statische Felder Werttyp Inline initialisieren](../code-quality/ca2207-initialize-value-type-static-fields-inline.md) | Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor. |
| CA2208 |[CA2208: Argumentausnahmen korrekt instanziieren](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md) | Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird. |
| CA2210 |[CA2210: Assemblys müssen gültige starke Namen aufweisen.](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md) | Der starke Name schützt Clients vor dem versehentlichen Laden einer manipulierten Assembly. Assemblys ohne starke Namen sollten nur in ganz bestimmten Szenarien bereitgestellt werden. Wenn Sie nicht einwandfrei signierte Assemblys freigeben oder verteilen, kann die Assembly manipuliert werden, die Common Language Runtime lädt die Assembly unter Umständen nicht, oder der Benutzer muss die Überprüfung auf dem Computer deaktivieren. |
| CA2211 |[CA2211: Nicht konstante Felder sollten nicht sichtbar sein.](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md) | Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Der Zugriff auf ein solches Feld muss sorgfältig kontrolliert werden und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt. |
| CA2212 | [CA2212: Nicht verarbeitete Komponenten mit WebMethod markieren](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md) |Eine Methode in einem Typ, der von System.EnterpriseServices.ServicedComponent erbt, wird mit System.Web.Services.WebMethodAttribute markiert. Da das Verhalten von WebMethodAttribute und einer ServicedComponent-Methode sowie deren Anforderungen an den Kontext sowie den Transaktionsablauf zu Konflikten führen, ist das Verhalten der Methode in bestimmten Szenarien fehlerhaft. |
| CA2213 | [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen. |
| CA2214 | [CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md) | Wenn ein Konstruktor eine virtuelle Methode aufruft, wurde möglicherweise der Konstruktor für die Instanz, von der die Methode aufgerufen wird, nicht ausgeführt. |
| CA2215 | [CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md) | Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden. |
| CA2216 |[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md) | Ein Typ, der System.IDisposable implementiert und Felder besitzt, bei denen die Verwendung nicht verwalteter Ressourcen empfohlen wird, implementiert keinen Finalizer wie von Object.Finalize beschrieben. |
| CA2217 | [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md) |Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und weist einen oder mehrere Werte auf, die keine Potenzen von 2 und keine Kombination von anderen in der Enumeration definierten Werten bilden. |
| CA2218 |[CA2218: Überschreiben von GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md) | GetHashCode gibt einen Wert auf der Grundlage der aktuellen Instanz zurück, die sich für Hashalgorithmen und Datenstrukturen eignet, z. B. für eine Hashtabelle. Zwei Objekte, die denselben Typ aufweisen und gleich sind, müssen den gleichen Hashcode zurückgeben. |
| CA2219 | [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2220 | [CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md) | Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu garantieren, müssen die Typen die Finalize-Methode ihrer Basisklasse in der eigenen Finalize-Methode aufrufen. |
| CA2221 |[CA2221: Finalizer sollten geschützt sein](../code-quality/ca2221-finalizers-should-be-protected.md) | Finalizer müssen den Familienzugriffsmodifizierer verwenden. |
| CA2222 | [CA2222: Sichtbarkeit für geerbte Member nicht verringern](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md) |Sie sollten den Zugriffsmodifizierer für geerbte Member nicht ändern. Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert. |
| CA2223 | [CA2223: Member sollten sich durch mehr als den Rückgabetyp unterscheiden.](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md) | Die Common Language Runtime lässt die Verwendung von Rückgabetypen zu, mit deren Hilfe zwischen anderweitig identischen Membern unterschieden werden kann. Trotzdem ist diese Funktion nicht in der Common Language Specification (CLS) enthalten und keine gebräuchliche Funktion von .NET-Programmiersprachen. |
| CA2224 | [CA2224: Außerkraftsetzung equals, Equals beim Überladen](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md) | Ein öffentlicher Typ implementiert den Gleichheitsoperator, überschreibt jedoch Object.Equals nicht. |
| CA2225 | [CA2225: Operatorüberladungen weisen benannte alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md) |Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternativmember gewährt auf die gleiche Funktionalität wie der Operator Zugriff und wird für Entwickler bereitgestellt, die in Sprachen programmieren, in denen überladene Operatoren nicht unterstützt werden. |
| CA2226 | [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md) | Ein Typ implementiert den Gleichheits- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren. |
| CA2227 |[CA2227: Sammlungseigenschaften sollten schreibgeschützt sein](../code-quality/ca2227-collection-properties-should-be-read-only.md) |Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. |
| CA2228 | [CA2228: Führen Sie nicht freigegebene Ressourcenformate](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md) | Ressourcendateien, die mithilfe von Vorabversionen von .NET Framework erstellt wurden, möglicherweise nicht von den unterstützten Versionen von .NET Framework verwendet werden. |
| CA2229 | [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md) | Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor. |
| CA2230 | [CA2230: Params für Variablenargumente verwenden](../code-quality/ca2230-use-params-for-variable-arguments.md) | Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die statt des params-Schlüsselworts die VarArgs-Aufrufkonvention verwendet. |
| CA2231 | [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Ein Werttyp überschreibt Object.Equals, implementiert jedoch nicht den Gleichheitsoperator. |
| CA2232 | [CA2232: Mark Windows Forms-Einstiegspunkte mit STAThread markieren](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md) | STAThreadAttribute gibt an, dass das COM-Threadingmodell für die Anwendung ein Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. |
| CA2233 |[CA2233: Vorgänge sollten nicht überlaufen](../code-quality/ca2233-operations-should-not-overflow.md) | Sie sollten keine arithmetischen Operationen ausführen, ohne zuerst die Operanden zu überprüfen. Dies stellt sicher, dass das Ergebnis der Operation nicht außerhalb des Bereichs möglicher Werte für die beteiligten Datentypen liegt. |
| CA2234 | [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md) | Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält. Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt. |
| CA2235 | [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md) | Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert. |
| CA2236 | [CA2236: Aufrufen von Basisklassenmethoden auf ISerializable-Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) | Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die GetObjectData-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder im Konstruktor des entsprechenden abgeleiteten Typs auf. |
| CA2237 | [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) | Damit Typen von der Common Language Runtime als serialisierbar erkannt werden, müssen sie mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der ISerializable-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet. |
| CA2238 |[CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md) | Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit. |
| CA2239 | [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) | Ein Typ verfügt über ein Feld, das mit dem System.Runtime.Serialization.OptionalFieldAttribute-Attribut gekennzeichnet ist, und gibt keine Methoden für die Deserialisierungsereignisbehandlung an. |
| CA2240 | [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md) | Um einen Verstoß gegen diese Regel zu beheben, stellen Sie sicher, dass die GetObjectData-Methode sichtbar und überschreibbar ist und dass alle Instanzenfelder in den Serialisierungsprozess einbezogen werden oder explizit mit dem NonSerializedAttribute-Attribut markiert sind. |
| CA2241 | [CA2241: Geben Sie Argumente für Formatierungsmethoden angeben](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md) | Das an System.String.Format übergebene format-Argument enthält keine Formatelemente, die den einzelnen Objektargumenten entsprechen oder umgekehrt. |
| CA2242 |[CA2242: Ordnungsgemäß auf NaN testen](../code-quality/ca2242-test-for-nan-correctly.md) | Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double). |
| CA2243 |[CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md) | Der Zeichenfolgenliteral-Parameter eines Attributs wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert. |
| CA5122 | [CA5122: P-Invoke-Deklarationen sollten nicht sicherungskritisch sein](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Methoden werden als SecuritySafeCritical markiert, wenn sie einen sicherheitsrelevanten Vorgang ausführen. Sie können jedoch auch mit transparentem Code verwendet werden. Transparenter Code ruft systemeigenen Code möglicherweise nie direkt mit P/Invoke auf. Wenn daher P/Invoke als sicherungskritisch markiert wird, kann es nicht von transparentem Code aufgerufen werden, was bei der Sicherheitsanalyse irreführend ist. |