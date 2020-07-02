---
title: Codeanalysewarnungen für verwalteten Code nach CheckId
ms.date: 04/18/2019
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
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
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
- CA1507
- CA1508
- CA1509
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
- CA1805
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
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1835
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
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
- CA2245
- CA2246
- CA2247
- CA5122
- CA5374
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3f8188a83a11811cc73a3b38c45df8dd7d27d1c1
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814809"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Code Analyse Warnungen für verwalteten Code nach CheckId

In der folgenden Tabelle werden Codeanalysewarnungen für verwalteten Code nach dem CheckId-Bezeichner der Warnung aufgeführt.

| CheckId | Warnung | BESCHREIBUNG |
|---------| - | - |
| CA1000 | [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000.md) | Wenn ein statischer Member eines generischen Typs aufgerufen wird, muss das Typargument für den Typ angegeben werden. Wenn ein generischer Instanzmember, der keine Unterstützung für Rückschlüsse bietet, aufgerufen wird, muss das Typargument für den Member angegeben werden. In diesen beiden Fällen ist die Syntax zum Angeben des Typarguments unterschiedlich und leicht zu verwechseln. |
| CA1001 | [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können.](../code-quality/ca1001.md) | Eine Klasse deklariert und implementiert ein Instanzenfeld, das den System.IDisposable-Typ aufweist, IDisposable jedoch nicht implementiert. Eine Klasse, die ein IDisposable-Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte die IDisposable-Schnittstelle implementieren. |
| CA1002 | [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002.md) | System. Collections. Generic. List< (of \<(T> ) >) ist eine generische Sammlung, die für Leistung und nicht Vererbung konzipiert ist. Daher enthält List keine virtuellen Member. Stattdessen sollten die generischen Auflistungen, die im Hinblick auf die Vererbung entworfen wurden, verfügbar gemacht werden. |
| CA1003 | [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003.md) |Ein Typ enthält einen Delegaten, der void zurückgibt. Die zugehörige Signatur enthält zwei Parameter (der erste ist ein Objekt, der zweite ein Typ, der EventArgs zugewiesen werden kann), und Microsoft .NET Framework 2.0 ist Ziel der enthaltenden Assembly. |
| CA1004 | [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004.md) | Mithilfe eines Rückschlusses wird das Typargument einer generischen Methode nach dem Typ des an die Methode übergebenen Arguments festgelegt, anstatt nach der expliziten Spezifikation des Typarguments. Um den Rückschluss zu aktivieren, muss die Parametersignatur einer generischen Methode einen Parameter einschließen, der vom selben Typ wie der Typparameter für die Methode ist. In diesem Fall muss das Typargument nicht angegeben werden. Wenn für alle Typparameter der Rückschluss verwendet wird, ist die Syntax zum Aufrufen von generischen und nicht generischen Instanzenmethoden identisch. Dies vereinfacht die Verwendung generischer Methoden. |
| CA1005 | [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005.md) | Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Es ist in der Regel offensichtlich mit einem Typparameter, wie in der Liste \<T> , und in bestimmten Fällen mit zwei Typparametern, wie im Wörterbuch \<TKey, TValue> . Mehr als zwei Typparameter hingegen bereiten den meisten Benutzern Schwierigkeiten. |
| CA1006 | [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006.md) | Ein geschachteltes Typargument ist ein Typargument, das auch ein generischer Typ ist. Um einen Member aufzurufen, dessen Signatur ein geschachteltes Typargument enthält, muss der Benutzer einen generischen Typ instanziieren und diesen an den Konstruktor eines zweiten generischen Typs übergeben. Die erforderliche Prozedur und die Syntax sind komplex, und diese Vorgehensweise sollte daher vermieden werden. |
| CA1007 |[CA1007: Nach Möglichkeit Generics verwenden.](../code-quality/ca1007.md) | Eine extern sichtbare Methode enthält einen Verweisparameter vom Typ System.Object. Bei Verwendung einer generischen Methode können alle Typen mit gewissen Einschränkungen an die Methode übergeben werden, ohne dass der Typ zuvor in den Typ des Verweisparameters umgewandelt werden muss. |
| CA1008 | [CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.](../code-quality/ca1008.md) | Der Standardwert einer nicht initialisierten Enumeration ist ebenso wie der anderer Werttypen 0 (null). Eine Enumeration ohne das Flags-Attribut sollte einen Member mit dem Wert 0 (null) definieren, damit der Standardwert ein gültiger Wert der Enumeration ist. Wenn eine Enumeration, auf die FlagsAttribute angewendet wird, einen Member mit dem Wert 0 (null) definiert, sollte dieser den Namen "None" haben, um anzugeben, dass in der Enumeration keine Werte festgelegt wurden. |
| CA1009 | [CA1009: Ereignishandler korrekt deklarieren.](../code-quality/ca1009.md) | Ereignishandlermethoden nehmen zwei Parameter an. Der erste ist vom Typ System.Object und hat den Namen "sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Typ System.EventArgs und hat den Namen "e". Dies sind die Daten, die dem Ereignis zugeordnet sind. Ereignishandlermethoden geben normalerweise keinen Wert zurück. In der Programmiersprache C# wird dies mit dem void-Rückgabetyp angegeben. |
| CA1010 | [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010.md) | Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Anschließend kann die Auflistung zum Auffüllen generischer Auflistungstypen verwendet werden. |
| CA1011 |[CA1011: Basistypen als Parameter übergeben.](../code-quality/ca1011.md) | Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden. Wenn die vom abgeleiteten Parametertyp bereitgestellte zusätzliche Funktionalität nicht erforderlich ist, lässt die Verwendung des Basistyps eine allgemeinere Nutzung der Methode zu. |
| CA1012 | [CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen.](../code-quality/ca1012.md) | Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen und Sie keine Instanzen eines abstrakten Datentyps erstellen können, ist ein abstrakter Datentyp mit einem öffentlichen Konstruktor fehlerhaft konzipiert. |
| CA1013 | [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.](../code-quality/ca1013.md) | Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren. |
| CA1014 | [CA1014: Assemblys mit CLSCompliantAttribute markieren.](../code-quality/ca1014.md) | In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Um guten Entwurfsprinzipien gerecht zu werden, muss bei allen Assemblys die CLS-Kompatibilität mit <xref:System.CLSCompliantAttribute> explizit angegeben werden. Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel. |
| CA1016 | [CA1016: Assemblys mit AssemblyVersionAttribute markieren.](../code-quality/ca1016.md) | .NET verwendet die Versionsnummer zur eindeutigen Identifizierung einer Assembly und zum Binden an Typen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden. |
| CA1017 | [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017.md) |Das ComVisibleAttribute-Attribut bestimmt, wie COM-Clients auf verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. Die COM-Sichtbarkeit kann für die gesamte Assembly festgelegt und anschließend für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut fehlt, ist der Inhalt der Assembly für COM-Clients sichtbar. |
| CA1018 | [CA1018: Attribute mit AttributeUsageAttribute markieren.](../code-quality/ca1018.md) | Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von AttributeUsageAttribute, um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. |
| CA1019 | [CA1019: Accessoren für Attributargumente definieren.](../code-quality/ca1019.md) | Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen. |
| CA1020 | [CA1020: Namespaces mit wenigen Typen vermeiden.](../code-quality/ca1020.md) | Stellen Sie sicher, dass jeder der Namespaces logisch organisiert ist und dass es einen zulässigen Grund dafür gibt, Typen in einen wenig gefüllten Namespace einzufügen. |
| CA1021 | [CA1021: out-Parameter vermeiden.](../code-quality/ca1021.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen dem out-Parameter und dem ref-Parametern oft unklar. |
| CA1023 | [CA1023: Indexer sollten nicht mehrdimensional sein.](../code-quality/ca1023.md) | Indexer, d. h. indizierte Eigenschaften, sollten einen einzelnen Index verwenden. Wegen mehrdimensionaler Indexer kann die Verwendbarkeit der Bibliothek deutlich abnehmen. |
| CA1024 | [CA1024: Nach Möglichkeit Eigenschaften verwenden.](../code-quality/ca1024.md) | Eine öffentliche oder geschützte Methode hat einen Namen, der mit "Get" beginnt. Sie nimmt keine Parameter an und gibt einen Wert zurück, bei dem es sich nicht um ein Array handelt. Die Methode ist möglicherweise als Eigenschaft geeignet. |
| CA1025 | [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen.](../code-quality/ca1025.md) | Verwenden Sie ein Parameterarray statt sich wiederholender Argumente, wenn die genaue Anzahl der Argumente nicht bekannt ist und diese Argumente vom gleichen Typ sind oder als gleicher Typ übergeben werden können. |
| CA1026 | [CA1026: Standardparameter sollten nicht verwendet werden.](../code-quality/ca1026.md) | Methoden, die Standardparameter verwenden, sind nach der CLS zulässig. Die CLS lässt jedoch zu, dass die Werte, die diesen Parametern zugewiesen sind, von Compilern ignoriert werden. Damit das gewünschte Verhalten in verschiedenen Programmiersprachen erhalten bleibt, müssen Methoden, die Standardparameter verwenden, durch Methodenüberladungen ersetzt werden, von denen die Standardparameter bereitgestellt werden. |
| CA1027 |[CA1027: Enumerationen mit FlagsAttribute markieren.](../code-quality/ca1027.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Wenden Sie FlagsAttribute auf eine Enumeration an, wenn deren benannte Konstanten sinnvoll kombiniert werden können. |
| CA1028 | [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Standardmäßig wird zum Speichern des konstanten Werts der System.Int32-Datentyp verwendet. Sie können diesen zugrunde liegenden Typ zwar ändern, in den meisten Szenarien ist dies jedoch weder notwendig noch empfehlenswert. |
| CA1030 | [CA1030: Nach Möglichkeit Ereignisse verwenden.](../code-quality/ca1030.md) |Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Wenn eine Methode auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen. |
| CA1031 | [CA1031: Allgemeine Ausnahmetypen nicht auffangen.](../code-quality/ca1031.md) | Allgemeine Ausnahmen sollten nicht abgefangen werden. Fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme in der letzten Anweisung des catch-Blocks erneut aus. |
| CA1032 |[CA1032: Standardausnahmekonstruktoren implementieren.](../code-quality/ca1032.md) | Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. |
| CA1033 | [CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.](../code-quality/ca1033.md) | Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an. |
| CA1034 | [CA1034: Geschachtelte Typen sollten nicht sichtbar sein.](../code-quality/ca1034.md) | Ein geschachtelter Typ ist ein Typ, der innerhalb des Gültigkeitsbereichs eines anderen Typs deklariert ist. Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails der enthaltenden Typen. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein. |
| CA1035 | [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.](../code-quality/ca1035.md) | Nach dieser Regel müssen ICollection-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den Object-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. Diese Regel geht davon aus, dass der Typ, der ICollection implementiert, diese Implementierung zur Verwaltung einer Auflistung von Instanzen eines Typs vornimmt, der stärker ist als Object. |
| CA1036 | [CA1036: Methoden bei vergleichbaren Typen überschreiben.](../code-quality/ca1036.md) |Ein öffentlicher oder geschützter Typ implementiert die System.IComparable-Schnittstelle. Er überschreibt Object.Equals nicht und überlädt auch nicht den sprachspezifischen Operator für gleich, ungleich, kleiner als und größer als. |
| CA1038 | [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.](../code-quality/ca1038.md) | Nach dieser Regel müssen IEnumerator-Implementierungen für die Current-Eigenschaft auch eine Version mit starker Typisierung angeben, damit die Benutzer den Rückgabewert nicht in den starken Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. |
| CA1039 | [CA1039: Listen weisen eine starke Typisierung auf.](../code-quality/ca1039.md) | Nach dieser Regel müssen IList-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den System.Object-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden. |
| CA1040 |[CA1040: Leere Schnittstellen vermeiden.](../code-quality/ca1040.md) | Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Daher definiert sie keinen Vertrag, der implementiert werden kann. |
| CA1041 | [CA1041: ObsoleteAttribute-Meldung bereitstellen.](../code-quality/ca1041.md) | Ein Typ oder Member wird mit einem System.ObsoleteAttribute-Attribut markiert, dessen ObsoleteAttribute.Message-Eigenschaft nicht angegeben wurde. Wenn ein mit ObsoleteAttribute markierter Typ oder Member kompiliert wird, wird die Message-Eigenschaft des Attributs angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. |
| CA1043 | [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.](../code-quality/ca1043.md) | Indexer (d. h. indizierte Eigenschaften) sollten ganzzahlige Typen oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. R. zum Indizieren von Datenstrukturen verwendet und erweitern den Einsatzbereich der Bibliothek. Die Verwendung des Object-Typs sollte auf die Fälle beschränkt werden, in denen der spezielle integrale oder Zeichenfolgentyp zur Entwurfszeit nicht angegeben werden kann. |
| CA1044 | [CA1044: Eigenschaften sollten nicht lesegeschützt sein.](../code-quality/ca1044.md) | Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Wenn ein Benutzer einen Wert festlegen kann, bietet es keinerlei Sicherheitsvorteile, das Lesen und Anzeigen des Werts durch den Benutzer zu sperren. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird. |
| CA1045 |[CA1045: Typen nicht als Verweis übergeben.](../code-quality/ca1045.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Bibliotheks Architekten, die für eine allgemeine Zielgruppe entwerfen, sollten nicht erwarten, dass Benutzer die Arbeit mit- `out` oder- `ref` Parametern meistern. |
| CA1046 | [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046.md) | Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen. |
| CA1047 |[CA1047: Geschützte Member in versiegelten Typen nicht deklarieren.](../code-quality/ca1047.md) | Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können. Per Definition kann von versiegelten Typen nicht geerbt werden. Dies bedeutet, dass geschützte Methoden für versiegelte Typen nicht aufgerufen werden können. |
| CA1048 | [CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren.](../code-quality/ca1048.md) | Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Per Definition kann ein versiegelter Typ nicht geerbt werden. Dadurch wird eine virtuelle Methode für einen versiegelten Typ bedeutungslos. |
| CA1049 | [CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können.](../code-quality/ca1049.md) | Typen, die nicht verwaltete Ressourcen zuordnen, müssen IDisposable implementieren, damit Aufrufer diese Ressourcen bei Bedarf freigeben und die Lebensdauer der Objekte verkürzen können, die diese Ressourcen verwenden. |
| CA1050 | [CA1050: Typen in Namespaces deklarieren.](../code-quality/ca1050.md) | Typen werden in Namespaces deklariert, um Namenskonflikte zu verhindern und um verwandte Typen in einer Objekthierarchie zu organisieren. |
| CA1051 | [CA1051: Sichtbare Instanzfelder nicht deklarieren.](../code-quality/ca1051.md) | Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder sollten privat oder intern sein und durch die Verwendung von Eigenschaften verfügbar gemacht werden. |
| CA1052 | [CA1052: Statische Haltertypen sollten versiegelt sein.](../code-quality/ca1052.md) | Ein öffentlicher oder geschützter Typ enthält nur statische Member und wird nicht mit dem sealed (C#-Referenz)-Modifizierer (NotInheritable) deklariert. Ein Typ, der nicht geerbt werden soll, sollte mit dem sealed-Modifizierer markiert werden, um seine Verwendung als Basistyp zu verhindern. |
| CA1053 |[CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053.md) | Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor. Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Die Zeichenfolgenüberladung sollte die URI-Überladung aus Sicherheitsgründen mit dem Zeichenfolgenargument aufrufen. |
| CA1054 | [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054.md) | Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, sollte eine entsprechende Überladung angegeben werden, die eine Instanz der URI-Klasse annimmt, die diese Dienste auf sichere Weise bereitstellt. |
| CA1055 | [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055.md) | Diese Regel geht davon aus, dass die Methode einen URI zurückgibt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1056 | [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056.md) | Diese Regel geht davon aus, dass die Eigenschaft einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1057 | [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.](../code-quality/ca1057.md) | Ein Typ deklariert Methodenüberladungen, die sich nur durch die Ersetzung eines Zeichenfolgenparameters mit einem System.Uri-Parameter unterscheiden. Die Überladung, die den Zeichenfolgenparameter akzeptiert, ruft nicht die Überladung auf, die den URI-Parameter akzeptiert. |
| CA1058 | [CA1058: Typen sollten bestimmte Basistypen nicht erweitern.](../code-quality/ca1058.md) | Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Verwenden Sie eine der Alternativen. |
| CA1059 |[CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen.](../code-quality/ca1059.md) | Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann. Damit der Member universell verwendet werden kann, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle. |
| CA1060 | [CA1060: P/Aufrufe in die NativeMethods-Klasse verschieben](../code-quality/ca1060.md) | Plattformaufrufmethoden, beispielsweise Methoden, die mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut gekennzeichnet sind, oder Methoden, die in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mithilfe des Declare-Schlüsselworts definiert wurden, greifen auf nicht verwalteten Code zu. Diese Methoden sollten der Klasse NativeMethods, SafeNativeMethods oder UnsafeNativeMethods angehören. |
| CA1061 |[CA1061: Basisklassenmethoden nicht ausblenden.](../code-quality/ca1061.md) | Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ verdeckt, wenn die Parametersignatur der abgeleiteten Methode sich nur hinsichtlich der Typen unterscheidet, die schwächer abgeleitet sind als die entsprechenden Typen in der Parametersignatur der Basismethode. |
| CA1062 | [CA1062: Argumente von öffentlichen Methoden validieren.](../code-quality/ca1062.md) | Alle an extern sichtbare Methoden übergebenen Verweisargumente sollten auf NULL überprüft werden. |
| CA1063 | [CA1063: IDisposable korrekt implementieren.](../code-quality/ca1063.md) | Alle IDisposable-Typen müssen das Dispose-Muster korrekt implementieren. |
| CA1064 | [CA1064: Ausnahmen sollten öffentlich sein.](../code-quality/ca1064.md) | Eine interne Ausnahme ist nur innerhalb ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme von <xref:System.Exception> , oder geerbt wird <xref:System.SystemException> <xref:System.ApplicationException> , verfügt der externe Code nicht über genügend Informationen, um zu wissen, was mit der Ausnahme zu tun ist. |
| CA1065 | [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen.](../code-quality/ca1065.md) | Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus. |
| CA1066 | [CA1066: „IEquatable“ beim Außerkraftsetzen von „Equals“ implementieren](../code-quality/ca1066.md) | Ein Werttyp überschreibt die- <xref:System.Object.Equals%2A> Methode, implementiert jedoch nicht <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: „Object.Equals(object)“ bei Implementierung von „IEquatable“ außer Kraft setzen](../code-quality/ca1067.md) | Ein Typ implementiert <xref:System.IEquatable%601> , aber überschreibt die- <xref:System.Object.Equals%2A> Methode nicht. |
| CA1068 | [CA1068: CancellationToken-Parameter müssen zuletzt aufgeführt werden.](../code-quality/ca1068.md) | Eine Methode verfügt über einen CancellationToken-Parameter, der nicht der letzte Parameter ist. |
| CA1069 | [CA1069: Enumerationen dürfen keine doppelten Werte aufweisen.](../code-quality/ca1069.md) | Eine Enumeration verfügt über mehrere Member, denen explizit derselbe Konstante Wert zugewiesen wird. |
| CA1070 | [CA1070: Ereignisfelder dürfen nicht als virtuell deklariert werden.](../code-quality/ca1070.md) | Ein [Feld ähnliches Ereignis](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) wurde als virtuell deklariert. |
| CA1200 | [CA1200: Verwenden Sie keine cref-Tags mit einem Präfix.](../code-quality/ca1200.md) | Das Attribut " [kref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) " in einem XML-Dokumenttag bedeutet "Code Verweis". Es gibt an, dass der innere Text des Tags ein Codeelement ist, wie z.B. ein Typ, eine Methode oder Eigenschaft. Vermeiden `cref` Sie die Verwendung von Tags mit Präfixen, da dies verhindert, dass der Compiler Verweise überprüft. Außerdem wird verhindert, dass die integrierte Entwicklungsumgebung (IDE) von Visual Studio diese Symbol Verweise bei refactoren findet und aktualisiert. |
| CA1300 | [CA1300: MessageBoxOptions angeben.](../code-quality/ca1300.md) | Wenn in Kulturen, in denen von rechts nach links gelesen wird, ein Meldungsfeld richtig angezeigt werden soll, müssen der RightAlign-Member und der RtlReading-Member der MessageBoxOptions-Enumeration an die Show-Methode übergeben werden. |
| CA1301 | [CA1301: Doppelte Zugriffstasten vermeiden.](../code-quality/ca1301.md) | Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffsschlüssel verfügen, ist das Verhalten des Zugriffsschlüssels nicht klar definiert. |
| CA1302 | [CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden.](../code-quality/ca1302.md) | Die System.Environment.SpecialFolder-Enumeration enthält Member, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können sich von Betriebssystem zu Betriebssystem unterscheiden. Der Benutzer kann einige Speicherorte ändern, und die Speicherorte sind lokalisiert. Die Environment.GetFolderPath-Methode gibt die der Environment.SpecialFolder-Enumeration zugeordneten Speicherorte zurück, die lokalisiert und für den derzeit ausgeführten Computer geeignet sind. |
| CA1303 | [CA1303: Literale nicht als lokalisierte Parameter übergeben.](../code-quality/ca1303.md) | Eine extern sichtbare Methode übergibt ein Zeichenfolgenliteralzeichen als Parameter an einen .net-Konstruktor oder eine Methode, und diese Zeichenfolge muss lokalisierbar sein. |
| CA1304 | [CA1304: CultureInfo angeben.](../code-quality/ca1304.md) | Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen System.Globalization.CultureInfo-Parameter akzeptiert. Die Methode oder der Konstruktor ruft nicht die Überladung auf, die den CultureInfo-Parameter akzeptiert. Wenn ein CultureInfo-Objekt oder ein System.IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1305 | [CA1305: IFormatProvider angeben.](../code-quality/ca1305.md) | Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen System.IFormatProvider-Parameter akzeptieren; die Methode oder der Konstruktor ruft die Überladung nicht auf, die den IFormatProvider-Parameter akzeptiert. Wenn ein System.Globalization.CultureInfo-Objekt oder ein IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1306 | [CA1306: Gebietsschema für Datentypen festlegen.](../code-quality/ca1306.md) | Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten wie die für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Wenn Sie eine DataTable oder ein DataSet erstellen, sollten Sie das Gebietsschema explizit festlegen. |
| CA1307 | [CA1307: StringComparison angeben.](../code-quality/ca1307.md) | Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein StringComparison-Parameter festgelegt wird. |
| CA1308 |[CA1308: Zeichenfolgen in Großbuchstaben normalisieren.](../code-quality/ca1308.md) | Zeichenfolgen sollten in Großschreibung normalisiert werden. Für eine kleine Gruppe von Zeichen wird bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt. |
| CA1309 | [CA1309: Ordinal-StringComparison verwenden.](../code-quality/ca1309.md) | Durch einen nicht linguistischen Zeichenfolgenvergleich wird der StringComparison-Parameter nicht auf Ordinal und nicht auf OrdinalIgnoreCase festgelegt. Wenn der Parameter explizit auf StringComparison.Ordinal oder StringComparison.OrdinalIgnoreCase festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert. |
| CA1400 | [CA1400: P/aufrufende Einstiegspunkte müssen vorhanden sein](../code-quality/ca1400.md) |Eine öffentliche oder geschützte Methode wird mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut markiert. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. |
| CA1401 | [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401.md) | Eine öffentliche oder geschützte Methode in einem öffentlichen Typ enthält das System.Runtime.InteropServices.DllImportAttribute-Attribut (in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] auch durch das Declare-Schlüsselwort implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| CA1402 |[CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden.](../code-quality/ca1402.md) | Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem dem Namen ein Unterstrich (_) und eine ganze Zahl angefügt werden, die der Reihenfolge der Deklaration der Überladung entspricht. |
| CA1403 | [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.](../code-quality/ca1403.md) | Ein COM-sichtbarer Werttyp wird mit dem System. Runtime. InteropServices. StructLayoutAttribute-Attribut gekennzeichnet, das auf LayoutKind. Auto festgelegt ist. Das Layout dieser Typen kann sich Zwischenversionen von .net ändern, wodurch com-Clients, die ein bestimmtes Layout erwarten, unterbricht werden. |
| CA1404 | [CA1404: GetLastError unmittelbar nach P/aufrufen aufrufen](../code-quality/ca1404.md) | Die Marshal. GetLastWin32Error-Methode oder die entsprechende [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError-Funktion wird aufgerufen, und der unmittelbar vorherige Aufruf erfolgt nicht an eine Betriebssystem Aufruf Methode. |
| CA1405 | [CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein.](../code-quality/ca1405.md) | Ein für COM sichtbarer Typ wird von einem Typ abgeleitet, der nicht für COM sichtbar ist. |
| CA1406 |[CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.](../code-quality/ca1406.md) | Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen. |
| CA1407 |[CA1407: Statische Member in für COM sichtbaren Typen vermeiden.](../code-quality/ca1407.md) | COM unterstützt keine statischen Methoden. |
| CA1408 | [CA1408: AutoDual ClassInterfaceType nicht verwenden.](../code-quality/ca1408.md) | Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. Standardmäßig wird eine auf Dispatch beschränkte Schnittstelle verwendet, wenn das ClassInterfaceAttribute-Attribut nicht angegeben wird. |
| CA1409 | [CA1409: Für COM sichtbare Typen müssen erstellt werden können.](../code-quality/ca1409.md) |Ein Verweistyp, der speziell als für COM sichtbar gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, jedoch keinen öffentlichen (parameterlosen) Standardkonstruktor. Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht von COM-Clients erstellt werden. |
| CA1410 | [CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410.md) | Ein Typ deklariert eine mit dem System.Runtime.InteropServices.ComRegisterFunctionAttribute-Attribut markierte Methode, aber keine mit dem System.Runtime.InteropServices.ComUnregisterFunctionAttribute-Attribut markierte Methode oder umgekehrt. |
| CA1411 | [CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411.md) | Eine mit dem System.Runtime.InteropServices.ComRegisterFunctionAttribute-Attribut oder dem System.Runtime.InteropServices.ComUnregisterFunctionAttribute-Attribut markierte Methode ist extern sichtbar. |
| CA1412 | [CA1412: ComSource-Schnittstellen als IDispatch markieren.](../code-quality/ca1412.md) | Ein Typ ist mit dem System.Runtime.InteropServices.ComSourceInterfacesAttribute-Attribut markiert, und mindestens eine der angegebenen Schnittstellen ist nicht mit dem auf ComInterfaceType.InterfaceIsIDispatch festgelegten System.Runtime.InteropServices.InterfaceTypeAttribute-Attribut markiert. |
| CA1413 | [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.](../code-quality/ca1413.md) | Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt der Felder auf Informationen, die nicht verfügbar gemacht werden sollen oder unbeabsichtigte Auswirkungen auf Design oder Sicherheit haben. |
| CA1414 | [CA1414: Boolesche P/aufrufen-Argumente mit MarshalAs markieren](../code-quality/ca1414.md) | Der boolesche Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. |
| CA1415 | [CA1415: "P/" korrekt deklarieren](../code-quality/ca1415.md) | Diese Regel sucht nach Deklarationen für eine Aufrufmethode des Betriebssystems, die [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]-Funktionen mit einem Zeiger auf einen OVERLAPPED-Strukturparameter zum Ziel haben, der zugehörige verwaltete Parameter ist jedoch kein Zeiger auf eine System.Threading.NativeOverlapped-Struktur. |
| CA1500 | [CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen.](../code-quality/ca1500.md) | Mit einer Instanzenmethode wird ein Parameter oder eine lokale Variable deklariert, dessen bzw. deren Name mit dem Namen eines Instanzenfelds des deklarierenden Typs übereinstimmt. Dies führt zu Fehlern. |
| CA1501 | [CA1501: Übermäßige Vererbung vermeiden.](../code-quality/ca1501.md) | Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. |
| CA1502 | [CA1502: Übermäßige Komplexität vermeiden.](../code-quality/ca1502.md) | Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird. |
| CA1504 | [CA1504: Irreführende Feldnamen überprüfen.](../code-quality/ca1504.md) | Der Name eines Instanzenfelds beginnt mit "s_", oder der Name eines static-Felds (Shared-Feld in Visual Basic) beginnt mit "m_". |
| CA1505 | [CA1505: Nicht wartbaren Code vermeiden.](../code-quality/ca1505.md) | Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre. |
| CA1506 | [CA1506: Übermäßige Klassenkopplungen vermeiden.](../code-quality/ca1506.md) | Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden. |
| CA1507 | [CA1507: „nameof“ anstelle der Zeichenfolge verwenden](../code-quality/ca1507.md) | Ein Zeichenfolgenliterals wird als Argument verwendet, bei dem ein- `nameof` Ausdruck verwendet werden kann. |
| CA1508 | [CA1508: Toten Bedingungscode vermeiden](../code-quality/ca1508.md) | Eine Methode verfügt über bedingten Code, der immer zu oder zur Laufzeit ausgewertet wird `true` `false` . Dies führt zu einem unzustellbaren Code in der `false` Verzweigung der Bedingung. |
| CA1509 | [CA1509: Ungültiger Eintrag in der Konfigurationsdatei für die Codemetrik.](../code-quality/ca1509.md) | Code metrikregeln, wie z. b. [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) und [CA1506](ca1506.md), haben eine Konfigurationsdatei mit dem Namen mit `CodeMetricsConfig.txt` einem ungültigen Eintrag bereitgestellt. |
| CA1600 | [CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle".](../code-quality/ca1600.md) | Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus. |
| CA1601 | [CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern.](../code-quality/ca1601.md) | Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden. |
| CA1700 | [CA1700: Enumerationswerte nicht mit "Reserviert" benennen.](../code-quality/ca1700.md) | Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. |
| CA1701 | [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1701.md) | Jeder Begriff in der Ressourcenzeichenfolge wird basierend auf der Groß-/Kleinschreibung in einzelne Token unterteilt. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. |
| CA1702 | [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1702.md) | Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung. |
| CA1703 | [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.](../code-quality/ca1703.md) | Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA1704 | [CA1704: Bezeichner sollten korrekt geschrieben werden.](../code-quality/ca1704.md) | Der Name eines extern sichtbaren Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA1707 | [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707.md) | Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft. |
| CA1708 | [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708.md) | Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen. |
| CA1709 | [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709.md) | Gemäß der Konvention werden Parameternamen in Kamel-Schreibweise verfasst, für Namespace-, Typ- und Membernamen wird die Pascal-Schreibweise verwendet. |
| CA1710 | [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.](../code-quality/ca1710.md) |Die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen weisen stets ein Suffix auf, das mit dem Basistyp oder der Schnittstelle verknüpft ist. |
| CA1711 | [CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711.md) | Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden. |
| CA1712 | [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.](../code-quality/ca1712.md) | Den Namen von Enumerationsmembern wird der Typname nicht als Präfix vorangestellt, da die Typinformationen von den Entwicklungswerkzeugen bereitgestellt werden sollten. |
| CA1713 | [CA1713: Ereignisse sollten kein Before- oder After-Präfix aufweisen.](../code-quality/ca1713.md) | Der Name eines Ereignisses beginnt mit "Before" oder "After". Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben. |
| CA1714 | [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714.md) | Eine öffentliche Enumeration verfügt über das System.FlagsAttribute-Attribut, und der Name endet nicht in der Pluralform ("s"). Die Namen von mit FlagsAttribute markierten Typen stehen im Plural, da das Attribut angibt, dass mehr als ein Wert festgelegt werden kann. |
| CA1715 | [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.](../code-quality/ca1715.md) | Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem großen "I". Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit einem großen "T". |
| CA1716 | [CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.](../code-quality/ca1716.md) | Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein. Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind. |
| CA1717 | [CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1717.md) | Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können. |
| CA1719 | [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719.md) | Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek. |
| CA1720 |[CA1720: Bezeichner dürfen keine Typnamen enthalten.](../code-quality/ca1720.md) | Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen. |
| CA1721 | [CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.](../code-quality/ca1721.md) |Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get"-Methoden und -Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen. |
| CA1722 | [CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722.md) | Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen. |
| CA1724 | [CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.](../code-quality/ca1724.md) | Typnamen sollten nicht mit den Namen von .NET-Namespaces identisch sein. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden. |
| CA1725 | [CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen.](../code-quality/ca1725.md) | Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt. |
| CA1726 | [CA1726: Bevorzugte Begriffe verwenden.](../code-quality/ca1726.md) | Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Der Name kann auch den Begriff "Flag" oder "Flags" enthalten. |
| CA1800 | [CA1800: Keine unnötigen Umwandlungen.](../code-quality/ca1800.md) | Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. |
| CA1801 | [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801.md) | Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. |
| CA1802 |[CA1802: Nach Möglichkeit Literale verwenden.](../code-quality/ca1802.md) |Ein Feld wird als static und read-only deklariert (Shared und ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) und mit einem Wert initialisiert, der zur Kompilierungszeit berechnet werden kann. Da der Wert, der dem Zielfeld zugewiesen ist, zur Kompilierzeit komprimiert werden kann, ändern Sie die Deklaration in ein Konstantenfeld (Konstanten in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), sodass der Wert zur Kompilierzeit anstelle der Laufzeit berechnet wird. |
| CA1804 | [CA1804: Nicht verwendete lokale Variablen entfernen.](../code-quality/ca1804.md) | Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung. |
| CA1805 | [CA1805: nicht unnötig initialisieren](../code-quality/ca1805.md) | Die .NET-Laufzeit initialisiert alle Felder von Verweis Typen mit ihren Standardwerten, bevor der Konstruktor ausgeführt wird. In den meisten Fällen ist das explizite Initialisieren eines Felds auf seinen Standardwert redundant, wodurch Wartungskosten erhöht und die Leistung beeinträchtigt werden kann (z. b. mit erhöhter assemblygröße). |
| CA1806 | [CA1806: Methodenergebnisse nicht ignorieren.](../code-quality/ca1806.md) | Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM-Methode oder P/Invoke-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird. |
| CA1809 |[CA1809: Übermäßige lokale Variablen vermeiden.](../code-quality/ca1809.md) | Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als Registrierung des Werts bezeichnet. Um die Wahrscheinlichkeit zu erhöhen, dass alle lokalen Variablen registriert werden, müssen Sie die Anzahl der lokalen Variablen auf 64 beschränken. |
| CA1810 | [CA1810: Statische Felder von Referenztypen inline initialisieren.](../code-quality/ca1810.md) | Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. |
| CA1811 | [CA1811: Nicht aufgerufenen privaten Code vermeiden.](../code-quality/ca1811.md) | Zu einem privaten oder internen Member (auf Assemblyebene) gibt es in der Assembly keine Aufrufer. Er wird nicht durch die Common Language Runtime und nicht durch einen Delegaten aufgerufen. |
| CA1812 | [CA1812: Nicht instanziierte interne Klassen vermeiden.](../code-quality/ca1812.md) | Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt. |
| CA1813 | [CA1813: Nicht versiegelte Attribute vermeiden.](../code-quality/ca1813.md) | .NET stellt Methoden zum Abrufen von benutzerdefinierten Attributen bereit. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Durch Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert. |
| CA1814 | [CA1814: Jagged Arrays mehrdimensionalen Arrays vorziehen.](../code-quality/ca1814.md) | Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird. |
| CA1815 | [CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben.](../code-quality/ca1815.md) | Bei Werttypen wird die Reflection-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. |
| CA1816 | [CA1816: GC.SuppressFinalize korrekt aufrufen.](../code-quality/ca1816.md) | Eine Methode, die eine Implementierung von Dispose bildet, ruft nicht GC.SuppressFinalize auf, oder eine Methode, die keine Implementierung von Dispose bildet, ruft GC.SuppressFinalize auf, oder eine Methode ruft GC.SuppressFinalize auf und übergibt ein anderes Element als dieses (Me in Visual Basic). |
| CA1819 | [CA1819: Eigenschaften sollten keine Arrays zurückgeben.](../code-quality/ca1819.md) | Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. |
| CA1820 | [CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.](../code-quality/ca1820.md) | Der Vergleich von Zeichenfolgen mit der String.Length-Eigenschaft oder der String.IsNullOrEmpty-Methode führt erheblich schneller zu Ergebnissen als das Verwenden von Equals. |
| CA1821 | [CA1821: Leere Finalizer entfernen.](../code-quality/ca1821.md) | Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Ein leerer Finalizer verursacht zusätzlichen Mehraufwand ohne Nutzen. |
| CA1822 |[CA1822: Member als statisch markieren.](../code-quality/ca1822.md) | Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen. |
| CA1823 | [CA1823: Nicht verwendete private Felder vermeiden.](../code-quality/ca1823.md) | Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt. |
| CA1824 |[CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren.](../code-quality/ca1824.md) | Das NeutralResourcesLanguage-Attribut informiert den Ressourcen-Manager über die Sprache, die zum Anzeigen der Ressourcen einer neutralen Kultur für eine Assembly verwendet wurde. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern. |
| CA1825 |[CA1825: Vermeiden Sie Arrayzuteilungen mit einer Länge von 0 (null).](../code-quality/ca1825.md) | Die Initialisierung eines Arrays der Länge 0 (null) führt zu einer unnötigen Speicher Belegung. Verwenden Sie stattdessen die statisch zugeordnete leere Array Instanz, indem Sie aufrufen <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Die Speicher Belegung wird für alle Aufrufe dieser Methode freigegeben. |
| CA1826 |[CA1826: Eigenschaft anstelle der LINQ-Enumerable-Methode verwenden.](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>Die LINQ-Methode wurde für einen Typ verwendet, der eine äquivalente, effizientere Eigenschaft unterstützt. |
| CA1827 |[CA1827: Count/LongCount nicht verwenden, wenn Any verwendet werden kann.](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>die-Methode oder die- <xref:System.Linq.Enumerable.LongCount%2A> Methode wurde verwendet, wenn die <xref:System.Linq.Enumerable.Any%2A> Methode effizienter wäre. |
| CA1828 |[CA1828: CountAsync/LongCountAsync nicht verwenden, wenn AnyAsync verwendet werden kann.](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>die-Methode oder die- <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> Methode wurde verwendet, wenn die <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> Methode effizienter wäre. |
| CA1829 |[CA1829: Length/Count-Eigenschaft anstelle der Enumerable.Count-Methode verwenden.](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>Die LINQ-Methode wurde für einen Typ verwendet, der eine äquivalente, effizientere oder-Eigenschaft unterstützt `Length` `Count` . |
| CA1830 |[CA1830: Bevorzugen Sie stark typisierte Append- und Insert-Methodenüberladungen für StringBuilder.](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A>und <xref:System.Text.StringBuilder.Insert%2A> Stellen über Ladungen für mehrere Typen über bereit <xref:System.String> .  Bevorzugen Sie nach Möglichkeit die stark typisierten über Ladungen über die Verwendung von ToString () und der Zeichen folgen basierten Überladung. |
| CA1831 |[CA1831: Verwenden Sie für Zeichenfolgen bei Bedarf anstelle von Range-basierten Indexern „AsSpan“.](../code-quality/ca1831.md) | Wenn Sie einen Range-Indexer für eine Zeichenfolge verwenden und den Wert dem Typ "Read onlyspan char" implizit zuweisen &lt; &gt; , wird die-Methode <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils der Zeichenfolge erzeugt wird. |
| CA1832 |[CA1832: Verwenden Sie „AsSpan“ oder „AsMemory“ anstelle von Range-basierten Indexern zum Abrufen eines ReadOnlySpan- oder ReadOnlyMemory-Teils eines Arrays.](../code-quality/ca1832.md) | Wenn Sie einen Range-Indexer für ein Array verwenden und den Wert implizit einem- <xref:System.ReadOnlySpan%601> oder- <xref:System.ReadOnlyMemory%601> Typ zuweisen, wird die-Methode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils des Arrays erzeugt wird. |
| CA1833 |[CA1833: Verwenden Sie „AsSpan“ oder „AsMemory“ anstelle von Range-basierten Indexern zum Abrufen eines Span- oder Memory-Teils eines Arrays.](../code-quality/ca1833.md) | Wenn Sie einen Range-Indexer für ein Array verwenden und den Wert implizit einem- <xref:System.Span%601> oder- <xref:System.Memory%601> Typ zuweisen, wird die-Methode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils des Arrays erzeugt wird. |
| CA1835 |[CA1835: bevorzugen Sie die "Memory"-basierten über Ladungen für "Read Async" und "schreiteasync".](../code-quality/ca1835.md) | ' Stream ' weist eine ' Schreib async '-Überladung auf, die ein ' Memory &lt; Byte &gt; ' als erstes Argument annimmt, und eine ' schreiteasync '-Überladung, die ein ' Read onlymemory &lt; Byte &gt; ' als erstes Argument annimmt. Bevorzugen Sie das Aufrufen der Speicher basierten über Ladungen, die effizienter sind. |
| CA1900 | [CA1900: Werttypfelder sollten portabel sein.](../code-quality/ca1900.md) | Anhand dieser Regel wird überprüft, ob die mit explizitem Layout deklarierten Strukturen korrekt ausgerichtet werden, wenn sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden. |
| CA1901 | [CA1901: P/Aufruf Deklarationen sollten portabel sein.](../code-quality/ca1901.md) | Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P/Invoke-Deklaration aus und überprüft die zugehörige Größe der Parameter beim Marshallen an nicht verwalteten Code unter einem 32-Bit- oder 64-Bit-Betriebssystem. |
| CA1903 | [CA1903: Nur API aus Zielframework verwenden.](../code-quality/ca1903.md) | Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist. |
| CA2000 | [CA2000: Objekte verwerfen, bevor Bereich verloren geht.](../code-quality/ca2000.md) | Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden. |
| CA2001 | [CA2001: Keine problematischen Methoden aufrufen.](../code-quality/ca2001.md) | Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf. |
| CA2002 |[CA2002: Auf Objekten mit schwacher Identität nicht sperren.](../code-quality/ca2002.md) |Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt. |
| CA2003 |[CA2003: Fibers nicht als Threads behandeln.](../code-quality/ca2003.md) | Ein verwalteter Thread wird als [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]-Thread behandelt. |
| CA2004 | [CA2004: Aufrufe an GC.KeepAlive entfernen.](../code-quality/ca2004.md) | Wenn Sie zur Verwendung von SafeHandle wechseln, entfernen Sie alle Aufrufe an GC.KeepAlive (Objekt). In diesem Fall sollten Klassen GC.KeepAlive nicht aufrufen müssen. Dabei wird davon ausgegangen, dass sie keinen Finalizer verwenden, sondern sich auf SafeHandle verlassen, um das Betriebssystemhandle zu beenden. |
| CA2006 | [CA2006: SafeHandle verwenden, um native Ressourcen zu kapseln.](../code-quality/ca2006.md) | Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist. |
| CA2007 | [CA2007: Eine Aufgabe nicht direkt abwarten](ca2007.md) | Eine asynchrone Methode [erwartet](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> direkt ein. Wenn eine asynchrone Methode <xref:System.Threading.Tasks.Task> direkt auf einen wartet, erfolgt die Fortsetzung in dem Thread, der die Aufgabe erstellt hat. Dieses Verhalten kann sich in Bezug auf die Leistung als kostspielig erweisen und kann zu einem Deadlock im UI-Thread führen. Rufen <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> Sie auf, um ihre Absicht für die Fortsetzung zu signalisieren. |
| CA2009 | [CA2009: „ToImmutableCollection“ nicht für einen ImmutableCollection-Wert aufrufen.](ca2009.md) | `ToImmutable`die Methode wurde für eine unveränderliche Auflistung aus dem <xref:System.Collections.Immutable> Namespace unnötig aufgerufen. |
| CA2011 | [CA2011: Eigenschaft nicht innerhalb ihres Setters zuweisen](ca2011.md) | Einer Eigenschaft wurde versehentlich ein Wert innerhalb ihrer eigenen [Set-Zugriffs](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)Methode zugewiesen. |
| CA2012 | [CA2012: Verwenden Sie ValueTasks ordnungsgemäß.](ca2012.md) | Valuetasks, die von Element aufrufen zurückgegeben wurden, sollen direkt gewartet werden.  Versucht, eine valuetask mehrmals zu verwenden oder direkt auf das Ergebnis zuzugreifen, bevor es als abgeschlossen bezeichnet wird, kann zu einer Ausnahme oder Beschädigung führen.  Das ignorieren einer solchen valuetask ist wahrscheinlich ein Hinweis auf einen Funktionsfehler und kann die Leistung beeinträchtigen. |
| CA2013 | [CA2013: Verwenden Sie ReferenceEquals nicht mit Werttypen.](ca2013.md) | Beim Vergleichen von Werten mit werden bei <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA und objB Werttypen verwendet, bevor Sie an die-Methode übermittelt werden <xref:System.Object.ReferenceEquals%2A> . Dies bedeutet, dass auch dann, wenn objA und objB dieselbe Instanz eines Werttyps darstellen, die <xref:System.Object.ReferenceEquals%2A> Methode trotzdem false zurückgibt. |
| CA2014 | [CA2014: Verwenden Sie stackzuweisung nicht in Schleifen.](ca2014.md) | Der von stackzugewiesc zugewiesene Stapel Speicher wird nur am Ende des Aufruf der aktuellen Methode freigegeben.  Die Verwendung in einer-Schleife kann zu unbegrenzten Stapel Vergrößerung und letztlichen Stapelüberlauf Bedingungen führen. |
| CA2015 | [CA2015: Finalizer nicht für Typen definieren, die von memorymanager &lt; T abgeleitet sind&gt;](ca2015.md) | Durch das Hinzufügen eines Finalizers zu einem von abgeleiteten Typ <xref:System.Buffers.MemoryManager%601> kann der Speicher freigegeben werden, während er noch von einem verwendet wird <xref:System.Span%601> . |
| CA2100 | [CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen.](../code-quality/ca2100.md) | Eine Methode legt die System.Data.IDbCommand.CommandText-Eigenschaft mithilfe einer Zeichenfolge fest, die aus einem Zeichenfolgenargument für die Methode erstellt wird. Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. |
| CA2101 |[CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101.md) | Ein Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling der Zeichenfolge durch. Auf diese Weise kann potenziell eine Sicherheitslücke verursacht werden. |
| CA2102 | [CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.](../code-quality/ca2102.md) | Ein Member in einer Assembly, die nicht mit dem RuntimeCompatibilityAttribute bzw. mit RuntimeCompatibility(WrapNonExceptionThrows = false) gekennzeichnet ist, enthält einen Catch-Block zur Behandlung von System.Exception und keinen unmittelbar folgenden allgemeinen Catch-Block. |
| CA2103 | [CA2103: Imperative Sicherheit überprüfen.](../code-quality/ca2103.md) |Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist. Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. |
| CA2104 |[CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren.](../code-quality/ca2104.md) | Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt. Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. |
| CA2105 | [CA2105: Arrayfelder dürfen nicht schreibgeschützt sein.](../code-quality/ca2105.md) |Wenn Sie den schreibgeschützten Modifizierer (ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) auf ein Feld mit einem Array anwenden, kann das Feld nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. |
| CA2106 | [CA2106: Sichere Bestätigungen.](../code-quality/ca2106.md) | Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt. Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. |
| CA2107 | [CA2107: Verwendung von Deny und PermitOnly überprüfen.](../code-quality/ca2107.md) |Die PermitOnly-Methode und die CodeAccessPermission. Deny-Sicherheitsaktionen sollten nur von denjenigen verwendet werden, die über erweiterte Kenntnisse der .NET-Sicherheit verfügen. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden. |
| CA2108 | [CA2108: Deklarative Sicherheit auf Werttypen überprüfen.](../code-quality/ca2108.md) | Ein öffentlicher oder geschützter Werttyp wird durch Datenzugriff oder Linkaufrufe gesichert. |
| CA2109 | [CA2109: Sichtbare Ereignishandler überprüfen.](../code-quality/ca2109.md) | Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt. Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist. |
| CA2111 |[CA2111: Zeiger sollten nicht sichtbar sein.](../code-quality/ca2111.md) | Ein Zeiger ist nicht privat, intern oder schreibgeschützt. Bösartiger Code kann den Wert des Zeigers ändern und damit potenziell Zugriffe auf beliebige Speicherbereiche ermöglichen oder Anwendungs- bzw. Systemfehler verursachen. |
| CA2112 | [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112.md) | Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird durch Linkaufrufe gesichert. Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen. |
| CA2114 | [CA2114: Methodensicherheit sollte Superset des Typs sein.](../code-quality/ca2114.md) | Eine Methode sollte bei der gleichen Aktion nicht sowohl auf einer Methodenebene als auch auf einer Typebene deklarative Sicherheit aufweisen. |
| CA2115 | [CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.](../code-quality/ca2115.md) | Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird. |
| CA2116 | [CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.](../code-quality/ca2116.md) |Wenn eine voll vertrauenswürdige Assembly über das APTCA-Attribut (AllowPartiallyTrustedCallersAttribute) verfügt und die Assembly Code in einer anderen Assembly ausführt, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden. |
| CA2117 | [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.](../code-quality/ca2117.md) | Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein in der Assembly enthaltener Typ von einem Typ erbt, der keine nicht voll vertrauenswürdigen Aufrufer zulässt, dann können Sicherheitslücken entstehen, die sich für Angriffe ausnutzen lassen. |
| CA2118 | [CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen.](../code-quality/ca2118.md) |SuppressUnmanagedCodeSecurityAttribute ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code ausführen, der COM-Interop oder Betriebssystemaufrufe verwendet. Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. |
| CA2119 | [CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.](../code-quality/ca2119.md) | Ein vererbbarer öffentlicher Typ stellt eine überschreibbare Methodenimplementierung einer internen Schnittstelle (Friend in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) bereit. Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird. |
| CA2120 | [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120.md) | Dieser Typ verfügt über einen Konstruktor, der ein System.Runtime.Serialization.SerializationInfo-Objekt und ein System.Runtime.Serialization.StreamingContext-Objekt (die Signatur des Serialisierungskonstruktors) akzeptiert. Dieser Konstruktor ist nicht durch eine Sicherheitsüberprüfung gesichert. Dagegen ist mindestens einer der normalen Konstruktoren des Typs gesichert. |
| CA2121 | [CA2121: Statische Konstruktoren sollten privat sein.](../code-quality/ca2121.md) | Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird. Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist. Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen. |
| CA2122 | [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen.](../code-quality/ca2122.md) | Ein öffentlicher oder geschützter Member enthält Linkaufrufe und wird von einem Member aufgerufen, der keine Sicherheitsüberprüfungen ausführt. Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. |
| CA2123 | [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.](../code-quality/ca2123.md) | Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Bei einem Verstoß gegen diese Regel kann ein böswilliger Aufrufer den Linkaufruf einfach durch Aufruf der ungesicherten Methode umgehen. |
| CA2124 | [CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen.](../code-quality/ca2124.md) | Eine öffentliche oder geschützte Methode enthält einen try/finally-Block. Durch den finally-Block, der nicht wiederum in einen finally-Block eingeschlossen ist, wird der Sicherheitszustand zurückgesetzt. |
| CA2126 | [CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen.](../code-quality/ca2126.md) | Ein öffentlicher unversiegelter Typ wird durch einen Linkaufruf geschützt und verfügt über eine überschreibbare Methode. Weder der Typ noch die Methode wird mit einer Vererbungsanforderung geschützt. |
| CA2130 | [CA2130: Sicherheitskritische Konstanten sollten transparent sein.](../code-quality/ca2130.md) | Transparenzerzwingung wird nicht für konstante Werte erzwungen, da Compiler konstante Werte inline verwenden, damit zur Laufzeit keine Suche erforderlich ist. Konstante Felder sollten sicherheitstransparent sein, damit Codebearbeiter nicht davon ausgehen, dass dieser transparente Code nicht auf die Konstante zugreifen kann. |
| CA2131 | [CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.](../code-quality/ca2131.md) | Ein Typ ist an Typäquivalenz beteiligt, und der Typ selbst oder ein Member oder Feld des Typs wird mit dem SecurityCriticalAttribute-Attribut markiert. Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an Typäquivalenz beteiligt sind. Wenn die CLR einen derartigen Typ erkennt, wird dieser nicht zur Laufzeit mit einem TypeLoadException-Objekt geladen. In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren, statt die Typäquivalenz von tlbimp und den Compilern ausführen zu lassen. |
| CA2132 | [CA2132: Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.](../code-quality/ca2132.md) |Typen und Member mit dem SecurityCriticalAttribute können nicht vom Silverlight-Anwendungscode verwendet werden. Sicherheitsrelevante Typen und Member können nur von vertrauenswürdigem Code in der .NET Framework for Silverlight-Klassenbibliothek verwendet werden. Da eine öffentliche oder geschützte Konstruktion in einer abgeleiteten Klasse mindestens die gleiche Transparenz aufweisen muss wie die zugehörige Basisklasse, können Klassen in einer Anwendung nicht von Klassen abgeleitet werden, die als SecurityCritical markiert sind. |
| CA2133 | [CA2133: Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.](../code-quality/ca2133.md) | Diese Warnung wird für Methoden ausgelöst, die einen mit dem SecurityCriticalAttribute markierten Delegaten an eine Methode binden, die transparent oder mit dem SecuritySafeCriticalAttribute markiert ist. Die Warnung wird auch bei einer Methode ausgelöst, die einen transparenten oder sicherheitsrelevanten Delegaten an eine wichtige Methode bindet ist. |
| CA2134 | [CA2134: Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.](../code-quality/ca2134.md) |Diese Regel wird ausgelöst, wenn eine mit dem SecurityCriticalAttribute markierte Methode eine Methode überschreibt, die transparent oder mit dem SecuritySafeCriticalAttribute markiert ist. Die Regel wird auch ausgelöst, wenn eine transparente oder mit dem SecuritySafeCriticalAttribute markierte Methode eine Methode überschreibt, die mit dem SecurityCriticalAttribute markiert ist. Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird. |
| CA2135 | [CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.](../code-quality/ca2135.md) | LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Markieren Sie, statt LinkDemands zur Erzwingung von Sicherheit zur JIT-Kompilierungszeit zu erzwingen, die Methoden, Typen und Felder mit dem SecurityCriticalAttribute-Attribut. |
| CA2127 | [CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.](../code-quality/ca2136.md) | Kritischer Code kann nicht in einer mit 100 Prozent transparenten Assembly auftreten. Diese Regel analysiert 100 Prozent transparente Assemblys für alle SecurityCritical-Anmerkungen auf Typ-, Feld-und Methoden Ebene. |
| CA2136 | [CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.](../code-quality/ca2136.md) | Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen. Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind. Eine Klasse, die mit dem SecurityCriticalAttribute-Attribut markiert ist, kann z. B. keine Methode enthalten sein, die mit dem SecuritySafeCriticalAttribute-Attribut markiert ist. |
| CA2137 | [CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.](../code-quality/ca2137.md) | Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück. Diese Regel wird bei Versuchen von sicherheitstransparentem Code ausgelöst, nicht überprüfbare MISL (Microsoft Intermediate Language) auszuführen. Die Regel enthält jedoch kein vollständiges IL-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL-Überprüfung abzufangen. |
| CA2138 | [CA2138: Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.](../code-quality/ca2138.md) | Eine sicherheitstransparente Methode ruft eine Methode auf, die mit dem SuppressUnmanagedCodeSecurityAttribute-Attribut markiert ist. |
| CA2139 | [CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.](../code-quality/ca2139.md) | Diese Regel wird von jeder Methode ausgelöst, die transparent ist und versucht, eine prozessdestabilisierende Ausnahme mit dem HandleProcessCorruptedStateExceptionsAttribute-Attribut zu behandeln. Eine Ausnahme, die einen Prozess beschädigt, entspricht einer Ausnahme der CLR Version 4.0-Ausnahmeklassifizierung wie AccessViolationException. Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. |
| CA2129 | [CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.](../code-quality/ca2140.md) | Mit SecurityTransparentAttribute markierte Methoden rufen nicht öffentliche Member auf, die als SecurityCritical markiert sind. Diese Regel analysiert alle Methoden und Typen in einer Assembly, die gemischt transparent/kritisch ist, und kennzeichnet alle Aufrufe aus transparentem Code an nicht öffentlichen kritischen Code, der nicht als SecurityTreatAsSafe gekennzeichnet ist. |
| CA2140 | [CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.](../code-quality/ca2140.md) | Ein Codeelement, das mit dem SecurityCriticalAttribute-Attribut markiert ist, ist sicherheitskritisch. Eine transparente Methode kann kein sicherheitskritisches Element verwenden. Wenn ein transparenter Typ versucht, einen sicherheitskritischen Typ zu verwenden, wird TypeAccessException, MethodAccessException oder FieldAccessException ausgelöst. |
| CA2141 |[CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen](../code-quality/ca2141.md) | Eine sicherheitstransparente Methode ruft eine Methode in einer Assembly auf, die nicht mit dem APTCA markiert ist, oder eine sicherheitstransparente Methode erfüllt einen LinkDemand für einen Typ oder eine Methode. |
| CA2142 | [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.](../code-quality/ca2142.md) | Diese Regel wird für transparente Methoden ausgelöst, die für den Zugriff LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. |
| CA2143 | [CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.](../code-quality/ca2143.md) | Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. |
| CA2144 | [CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden.](../code-quality/ca2144.md) | Die Sicherheitsüberprüfung für transparenten Code ist nicht so umfassend wie die Sicherheitsüberprüfung für wichtigen Code, da in transparentem Code keine sicherheitsrelevanten Aktionen ausgeführt werden können. Aus einem Bytearray geladene Assemblys könnten in transparentem Code nicht erkannt werden, und dieses Bytearray könnte kritischen oder wichtigeren sicherheitsgeschützten Code enthalten, der überwacht werden muss. |
| CA2145 | [CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden.](../code-quality/ca2145.md) | Methoden, die mit dem SuppressUnmanagedCodeSecurityAttribute-Attribut ergänzt wurden, weisen jeder aufrufenden Methode einen impliziten LinkDemand zu. Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist. Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit dem SecurityCriticalAttribute-Attribut verwendet, macht diese Anforderung für Aufrufer der Methode leichter zu erkennen. |
| CA2146 | [CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.](../code-quality/ca2146.md) | Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. |
| CA2128 |[CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.](../code-quality/ca2147.md) | Diese Regel analysiert alle Methoden und Typen in einer Assembly, die entweder 100 Prozent transparent oder gemischt transparent/kritisch ist, und gibt alle deklarativen oder imperativen Verwendungen von Assert an. |
| CA2147 |[CA2147: Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.](../code-quality/ca2147.md) | Als SecurityTransparentAttribute markiertem Code werden keine ausreichenden Berechtigungen für Assertions erteilt. |
| CA2149 | [CA2149: Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.](../code-quality/ca2149.md) | Diese Regel wird für jede transparente Methode ausgelöst, die direkt einen Aufruf in nativen Code ausführt (z. B. mit einem P/Invoke-Aufruf). Verstöße gegen diese Regel führen im Transparenzmodell der Ebene 2 zu einer MethodAccessException und im Transparenzmodell der Ebene 1 zu einer vollständigen Anforderung für UnmanagedCode. |
| CA2151 |[CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein.](../code-quality/ca2151.md) | Um sicherheitskritische Typen zu verwenden, muss der Code, der auf den Typ verweist, entweder sicherheitskritisch oder sicherungskritisch sein. Dies gilt auch, wenn der Verweis indirekt ist. Daher kann ein sicherheitstransparentes oder sicherungskritisches Feld irreführend sein, denn transparenter Code kann trotzdem nicht auf das Feld zugreifen. |
| CA2200 | [CA2200: Erneut ausführen, um Stapeldetails beizubehalten.](../code-quality/ca2200.md) | Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren. |
| CA2201 | [CA2201: Keine reservierten Ausnahmetypen auslösen.](../code-quality/ca2201.md) | Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2202 | [CA2202: Objekte nicht mehrmals verwerfen.](../code-quality/ca2202.md) |Eine Methodenimplementierung enthält Codepfade, die für dasselbe Objekt mehrere Aufrufe von System.IDisposable.Dispose oder einer Entsprechung von Dispose (z. B. einer Close()-Methode für bestimmte Typen) verursachen können. |
| CA2204 | [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen.](../code-quality/ca2204.md) | Ein Zeichenfolgenliteral in einem Methodentext enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird. |
| CA2205 | [CA2205: Verwaltete Entsprechungen der Win32 API verwenden.](../code-quality/ca2205.md) | Eine Methode zum Aufrufen eines Betriebssystems ist definiert, und eine .NET-Methode mit der entsprechenden Funktionalität ist verfügbar. |
| CA2207 | [CA2207: Statische Felder für Werttyp inline initialisieren.](../code-quality/ca2207.md) | Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor. |
| CA2208 |[CA2208: Argumentausnahmen korrekt instanziieren.](../code-quality/ca2208.md) | Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird. |
| CA2210 |[CA2210: Assemblys müssen gültige starke Namen aufweisen.](../code-quality/ca2210.md) | Der starke Name schützt Clients vor dem versehentlichen Laden einer manipulierten Assembly. Assemblys ohne starke Namen sollten nur in ganz bestimmten Szenarien bereitgestellt werden. Wenn Sie nicht einwandfrei signierte Assemblys freigeben oder verteilen, kann die Assembly manipuliert werden, die Common Language Runtime lädt die Assembly unter Umständen nicht, oder der Benutzer muss die Überprüfung auf dem Computer deaktivieren. |
| CA2211 |[CA2211: Nicht konstante Felder sollten nicht sichtbar sein.](../code-quality/ca2211.md) | Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Der Zugriff auf ein solches Feld muss sorgfältig kontrolliert werden und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt. |
| CA2212 | [CA2212: ServicedComponents nicht mit WebMethod markieren.](../code-quality/ca2212.md) |Eine Methode in einem Typ, der von System.EnterpriseServices.ServicedComponent erbt, wird mit System.Web.Services.WebMethodAttribute markiert. Da das Verhalten von WebMethodAttribute und einer ServicedComponent-Methode sowie deren Anforderungen an den Kontext sowie den Transaktionsablauf zu Konflikten führen, ist das Verhalten der Methode in bestimmten Szenarien fehlerhaft. |
| CA2213 | [CA2213: Verwerfbare Felder verwerfen.](../code-quality/ca2213.md) | Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen. |
| CA2214 | [CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.](../code-quality/ca2214.md) | Wenn ein Konstruktor eine virtuelle Methode aufruft, wurde möglicherweise der Konstruktor für die Instanz, von der die Methode aufgerufen wird, nicht ausgeführt. |
| CA2215 | [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.](../code-quality/ca2215.md) | Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden. |
| CA2216 |[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.](../code-quality/ca2216.md) | Ein Typ, der System.IDisposable implementiert und Felder besitzt, bei denen die Verwendung nicht verwalteter Ressourcen empfohlen wird, implementiert keinen Finalizer wie von Object.Finalize beschrieben. |
| CA2217 | [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217.md) |Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und weist einen oder mehrere Werte auf, die keine Potenzen von 2 und keine Kombination von anderen in der Enumeration definierten Werten bilden. |
| CA2218 |[CA2218: GetHashCode beim Überschreiben von Equals überschreiben.](../code-quality/ca2218.md) | GetHashCode gibt einen Wert auf der Grundlage der aktuellen Instanz zurück, die sich für Hashalgorithmen und Datenstrukturen eignet, z. B. für eine Hashtabelle. Zwei Objekte, die denselben Typ aufweisen und gleich sind, müssen den gleichen Hashcode zurückgeben. |
| CA2219 | [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.](../code-quality/ca2219.md) | Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2220 | [CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.](../code-quality/ca2220.md) | Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu garantieren, müssen die Typen die Finalize-Methode ihrer Basisklasse in der eigenen Finalize-Methode aufrufen. |
| CA2221 |[CA2221: Finalizer sollten geschützt sein.](../code-quality/ca2221.md) | Finalizer müssen den Familienzugriffsmodifizierer verwenden. |
| CA2222 | [CA2222: Sichtbarkeit für geerbte Member nicht verringern.](../code-quality/ca2222.md) |Sie sollten den Zugriffsmodifizierer für geerbte Member nicht ändern. Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert. |
| CA2223 | [CA2223: Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.](../code-quality/ca2223.md) | Die Common Language Runtime lässt die Verwendung von Rückgabetypen zu, mit deren Hilfe zwischen anderweitig identischen Membern unterschieden werden kann. Trotzdem ist diese Funktion nicht in der Common Language Specification (CLS) enthalten und keine gebräuchliche Funktion von .NET-Programmiersprachen. |
| CA2224 | [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224.md) | Ein öffentlicher Typ implementiert den Gleichheitsoperator, überschreibt jedoch Object.Equals nicht. |
| CA2225 | [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225.md) |Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternativmember gewährt auf die gleiche Funktionalität wie der Operator Zugriff und wird für Entwickler bereitgestellt, die in Sprachen programmieren, in denen überladene Operatoren nicht unterstützt werden. |
| CA2226 | [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226.md) | Ein Typ implementiert den Gleichheits- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren. |
| CA2227 |[CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.](../code-quality/ca2227.md) |Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. |
| CA2228 | [CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen.](../code-quality/ca2228.md) | Ressourcen Dateien, die mithilfe von vorab Versionen von .NET erstellt wurden, können möglicherweise nicht von unterstützten Versionen von .NET verwendet werden. |
| CA2229 | [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229.md) | Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor. |
| CA2230 | [CA2230: params für Variablenargumente verwenden.](../code-quality/ca2230.md) | Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die statt des params-Schlüsselworts die VarArgs-Aufrufkonvention verwendet. |
| CA2231 | [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231.md) | Ein Werttyp überschreibt Object.Equals, implementiert jedoch nicht den Gleichheitsoperator. |
| CA2232 | [CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.](../code-quality/ca2232.md) | STAThreadAttribute gibt an, dass das COM-Threadingmodell für die Anwendung ein Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. |
| CA2233 |[CA2233: Vorgänge sollten nicht überlaufen.](../code-quality/ca2233.md) | Sie sollten keine arithmetischen Operationen ausführen, ohne zuerst die Operanden zu überprüfen. Dies stellt sicher, dass das Ergebnis der Operation nicht außerhalb des Bereichs möglicher Werte für die beteiligten Datentypen liegt. |
| CA2234 | [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234.md) | Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält. Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt. |
| CA2235 | [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235.md) | Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert. |
| CA2236 | [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236.md) | Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die GetObjectData-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder im Konstruktor des entsprechenden abgeleiteten Typs auf. |
| CA2237 | [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237.md) | Damit Typen von der Common Language Runtime als serialisierbar erkannt werden, müssen sie mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der ISerializable-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet. |
| CA2238 |[CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238.md) | Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit. |
| CA2239 | [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239.md) | Ein Typ verfügt über ein Feld, das mit dem System.Runtime.Serialization.OptionalFieldAttribute-Attribut gekennzeichnet ist, und gibt keine Methoden für die Deserialisierungsereignisbehandlung an. |
| CA2240 | [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240.md) | Um einen Verstoß gegen diese Regel zu beheben, stellen Sie sicher, dass die GetObjectData-Methode sichtbar und überschreibbar ist und dass alle Instanzenfelder in den Serialisierungsprozess einbezogen werden oder explizit mit dem NonSerializedAttribute-Attribut markiert sind. |
| CA2241 | [CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.](../code-quality/ca2241.md) | Das an System.String.Format übergebene format-Argument enthält keine Formatelemente, die den einzelnen Objektargumenten entsprechen oder umgekehrt. |
| CA2242 |[CA2242: Ordnungsgemäß auf NaN testen.](../code-quality/ca2242.md) | Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double). |
| CA2243 |[CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.](../code-quality/ca2243.md) | Der Zeichenfolgenliteral-Parameter eines Attributs wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert. |
| CA2244 | [CA2244: Keine Initialisierungen indizierter Elemente duplizieren](../code-quality/ca2244.md) | Ein Objektinitialisierer verfügt über mehr als einen indizierten Elementinitialisierer mit demselben Konstanten Index. Alle außer der letzte Initialisierer sind redundant. |
| CA2245 | [CA2245: Keine Zuweisung einer Eigenschaft zu sich selbst](../code-quality/ca2245.md) | Eine Eigenschaft wurde versehentlich selbst zugewiesen. |
| CA2246 | [CA2246: Keine Zuweisung eines Symbols und seines Members in der gleichen Anweisung](../code-quality/ca2246.md) | Es wird nicht empfohlen, ein Symbol und dessen Member, d. h. ein Feld oder eine Eigenschaft, in derselben Anweisung zuzuweisen. Es ist nicht klar, ob der Element Zugriff dazu gedacht war, den alten Wert des Symbols vor der Zuweisung oder den neuen Wert aus der Zuweisung in dieser Anweisung zu verwenden. |
| CA2247 | [CA2247: das Argument, das an den TaskCompletionSource-Konstruktor übergeben wurde, sollte eine taskupationoptions-Enumeration anstelle der TaskContinuationOptions-Enumeration sein.](../code-quality/ca2247.md) | TaskCompletionSource verfügt über Konstruktoren, die taskkreationoptions verwenden, die die zugrunde liegende Aufgabe steuern, und Konstruktoren, die den Objektzustand annehmen, der in der Aufgabe gespeichert ist.  Das versehentliche übergeben von TaskContinuationOptions anstelle von taskkreationoptions führt dazu, dass der Aufruf die Optionen als Zustand behandelt. |
| CA5122 | [CA5122 P/Aufruf Deklarationen sollten nicht sicher kritisch sein](../code-quality/ca5122.md) | Methoden werden als SecuritySafeCritical markiert, wenn sie einen sicherheitsrelevanten Vorgang ausführen. Sie können jedoch auch mit transparentem Code verwendet werden. Transparenter Code ruft systemeigenen Code möglicherweise nie direkt mit P/Invoke auf. Wenn daher P/Invoke als sicherungskritisch markiert wird, kann es nicht von transparentem Code aufgerufen werden, was bei der Sicherheitsanalyse irreführend ist. |
| CA5359 | [CA5359 die Zertifikats Überprüfung nicht deaktivieren](../code-quality/ca5359.md) | Ein Zertifikat kann bei der Authentifizierung der Identität des Servers helfen. Clients sollten das Serverzertifikat überprüfen, um sicherzustellen, dass Anforderungen an den vorgesehenen Server gesendet werden. Wenn servercertifikatevalidationcallback immer zurück `true` gegeben wird, übergibt jedes Zertifikat die Validierung. |
| CA5360 | [CA5360 keine gefährlichen Methoden bei der Deserialisierung aufzurufen](../code-quality/ca5360.md) | Unsichere Deserialisierung ist ein Sicherheitsrisiko, das auftritt, wenn nicht vertrauenswürdige Daten verwendet werden, um die Logik einer Anwendung zu missbrauchen, einen Denial-of-Service-Angriff (DOS) zu verursachen oder sogar beliebigen Code auszuführen, wenn Sie deserialisiert werden. Es ist oft möglich, dass böswillige Benutzer diese deserialisierungsfeatures missbrauchen, wenn die Anwendung nicht vertrauenswürdige Daten deserialisiert, die unter ihrer Kontrolle liegen. Rufen Sie insbesondere gefährliche Methoden im Prozess der Deserialisierung auf. Erfolgreiche unsichere deserialisierungsangriffe können einem Angreifer ermöglichen, Angriffe wie DOS-Angriffe, Authentifizierungs Umgehungen und Remote Codeausführung auszuführen. |
| CA5362 | [CA5362 potenzieller Verweis Cycle im deserialisierten Objekt Diagramm](../code-quality/ca5362.md) | Wenn nicht vertrauenswürdige Daten deserialisiert werden, muss jeder Code, der das deserialisierte Objekt Diagramm verarbeitet, Verweis Zyklen verarbeiten, ohne in unendliche Schleifen zu wechseln. Dies umfasst sowohl Code, der Teil eines deserialisierungsrückrufs ist, als auch Code, der das Objekt Diagramm nach Abschluss der Deserialisierung verarbeitet. Andernfalls könnte ein Angreifer einen Denial-of-Service-Angriff mit bösartigen Daten durchführen, die einen Verweis-Cycle enthalten. |
| CA5365 | [CA5365 HTTP-Header Überprüfung nicht deaktivieren](../code-quality/ca5365.md) | Die HTTP-Header Überprüfung ermöglicht das Codieren von Wagen Rücklauf-und Zeilenumbruch Zeichen (\r und \n), die in Antwort Headern gefunden werden. Diese Codierung kann dabei helfen, Injection-Angriffe zu vermeiden, die eine Anwendung ausnutzen, die nicht vertrauenswürdige Daten in der Kopfzeile wieder gibt. |
| CA5366 | [CA5366 XmlReader für DataSet-Lese-XML verwenden](../code-quality/ca5366.md) | Wenn Sie ein-Element <xref:System.Data.DataSet> zum Lesen von XML mit nicht vertrauenswürdigen Daten verwenden, werden möglicherweise gefährliche externe Verweise geladen, die mithilfe von <xref:System.Xml.XmlReader> mit einem sicheren Konflikt Löser oder mit deaktivierter DTD-Verarbeitung eingeschränkt werden sollten. |
| CA5367 | [CA5367 Serialisieren Sie Typen mit Zeiger Feldern nicht.](../code-quality/ca5367.md) | Diese Regel überprüft, ob eine serialisierbare Klasse mit einem Zeiger Feld oder einer Eigenschaft vorhanden ist. Member, die nicht serialisiert werden können, können ein Zeiger sein, z. b. statische Member oder Felder, die mit gekennzeichnet sind <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set viewstatueuserkey für von Seite abgeleitete Klassen](../code-quality/ca5368.md) | Das Festlegen der- <xref:System.Web.UI.Page.ViewStateUserKey> Eigenschaft kann Ihnen helfen, Angriffe auf Ihre Anwendung zu verhindern, indem Sie der Ansichts Zustandsvariablen für einzelne Benutzer einen Bezeichner zuweisen können, sodass Angreifer die Variable nicht zum Generieren eines Angriffs verwenden können. Andernfalls gibt es Sicherheitsrisiken für die Website übergreifende Anforderungs Fälschung. |
| CA5374 | [CA5374 XslTransform nicht verwenden](../code-quality/ca5374.md) | Diese Regel überprüft, ob <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> im Code instanziiert wird. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>ist mittlerweile veraltet und sollte nicht verwendet werden. |
| CA5375 | [CA5375 Shared Access Signature für Konto nicht verwenden](../code-quality/ca5375.md) | Eine Konto-SAS kann den Zugriff auf Lese-, Schreib-und Löschvorgänge für BLOB-Container, Tabellen, Warteschlangen und Dateifreigaben delegieren, die mit einer Dienst-SAS nicht zulässig sind. Es unterstützt jedoch keine Richtlinien auf Container Ebene und bietet weniger Flexibilität und Kontrolle über die gewährten Berechtigungen. Wenn böswillige Benutzer diese erhalten haben, wird Ihr Speicherkonto problemlos kompromittiert. |
| CA5376 | [CA5376 Verwenden von sharedaccessproycol httpsonly](../code-quality/ca5376.md) | Bei SAS handelt es sich um sensible Daten, die nicht als Klartext über HTTP übertragen werden können. |
| CA5377 | [CA5377 verwenden der Zugriffs Richtlinie auf Container Ebene](../code-quality/ca5377.md) | Eine Zugriffs Richtlinie auf Container Ebene kann jederzeit geändert oder widerrufen werden. Sie bietet mehr Flexibilität und Kontrolle über die gewährten Berechtigungen. |
| CA5379 | [CA5379 verwenden Sie den Algorithmus für die schwache Schlüssel Ableitung nicht.](../code-quality/ca5379.md) | Die- <xref:System.Security.Cryptography.Rfc2898DeriveBytes> Klasse verwendet standardmäßig den- <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> Algorithmus. Sie sollten den Hash Algorithmus angeben, der in einigen über Ladungen des Konstruktors mit oder höher verwendet werden soll <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . Beachten Sie, dass <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> die-Eigenschaft nur über einen `get` -Accessor verfügt und keinen- `overriden` Modifizierer aufweist. |
| CA5382 | [CA5382 Verwenden von sicheren Cookies in ASP.net Core](../code-quality/ca5382.md) | Anwendungen, die über HTTPS verfügbar sind, müssen sichere Cookies verwenden, die dem Browser zeigen, dass das Cookie nur mit Secure Sockets Layer (SSL) übertragen werden soll. |
| CA5383 | [CA5383 sicherstellen der Verwendung von sicheren Cookies in ASP.net Core](../code-quality/ca5383.md) | Anwendungen, die über HTTPS verfügbar sind, müssen sichere Cookies verwenden, die dem Browser zeigen, dass das Cookie nur mit Secure Sockets Layer (SSL) übertragen werden soll. |
| CA5384 | [CA5384 verwenden Sie den Digital Signature-Algorithmus (DSA) nicht.](../code-quality/ca5384.md) | DSA ist ein schwacher Algorithmus für die asymmetrische Verschlüsselung. |
| CA5385 | [CA5385 use Rivest – Shamir – Adleman (RSA)-Algorithmus mit ausreichender Schlüsselgröße](../code-quality/ca5385.md) | Ein RSA-Schlüssel, der kleiner als 2048 Bits ist, ist anfälliger für Brute-Force-Angriffe. |
| CA5387 | [CA5387 verwenden Sie keine schwache Schlüssel abderivations Funktion mit unzureichender Iterations Anzahl.](../code-quality/ca5387.md) | Mit dieser Regel wird überprüft, ob von ein Kryptografieschlüssel <xref:System.Security.Cryptography.Rfc2898DeriveBytes> mit einer Iterations Anzahl von weniger als 100.000 generiert wurde. Eine höhere iterations Anzahl kann bei der Vermeidung von Wörterbuchangriffen helfen, die versuchen, den generierten kryptografischen Schlüssel zu erraten. |
| CA5388 | [CA5388 bei Verwendung der Funktion für die schwache Schlüssel Ableitung eine ausreichende Anzahl von Iterationen sicherstellen](../code-quality/ca5388.md) | Mit dieser Regel wird überprüft, ob von ein Kryptografieschlüssel <xref:System.Security.Cryptography.Rfc2898DeriveBytes> mit einer Iterations Anzahl generiert wurde, die möglicherweise kleiner als 100.000 ist. Eine höhere iterations Anzahl kann bei der Vermeidung von Wörterbuchangriffen helfen, die versuchen, den generierten kryptografischen Schlüssel zu erraten. |
| CA5390 | [CA5390 Verschlüsselungsschlüssel nicht hart codieren](../code-quality/ca5390.md) | Damit ein symmetrischer Algorithmus erfolgreich ist, muss der geheime Schlüssel nur dem Absender und dem Empfänger bekannt sein. Wenn ein Schlüssel hart codiert ist, kann er leicht erkannt werden. Selbst bei kompilierten Binärdateien ist es für böswillige Benutzer leicht, Sie zu extrahieren. Nachdem der private Schlüssel kompromittiert wurde, kann der Chiffre Text direkt entschlüsselt werden und ist nicht mehr geschützt. |
| CA5391 | [CA5391 Verwenden von antifälschungstoken in ASP.net Core MVC-Controllern](../code-quality/ca5391.md) | Das Verarbeiten einer- `POST` ,-,-oder-Anforderung, `PUT` `PATCH` `DELETE` ohne ein antifälschungstoken zu validieren, kann für Website übergreifende Anforderungs Fälschungs Angriffe anfällig sein. Mit einem Website übergreifenden Anforderungs Fälschungs Angriff können böswillige Anforderungen von einem authentifizierten Benutzer an Ihren ASP.net Core MVC-Controller gesendet werden. |
| CA5392 | [CA5392 Verwenden des defaultdllimportsearchpath-Attributs für P/Aufrufe](../code-quality/ca5392.md) | Standardmäßig verwenden P/aufrufen Funktionen, indem Sie <xref:System.Runtime.InteropServices.DllImportAttribute> eine Reihe von Verzeichnissen testen, einschließlich des aktuellen Arbeitsverzeichnisses für die zu ladende Bibliothek. Dies kann ein Sicherheitsproblem für bestimmte Anwendungen sein, was zu einer DLL-Hijacking-Aktion führt. |
| CA5393 | [CA5393 verwenden Sie keinen unsicheren dllimportsearchpath-Wert.](../code-quality/ca5393.md) | In den standardmäßigen dll-Such Verzeichnissen und Assemblyverzeichnissen könnte eine bösartige dll vorhanden sein. Abhängig davon, wo Ihre Anwendung ausgeführt wird, kann es sich auch um eine bösartige dll im Verzeichnis der Anwendung handeln. |
| CA5394 | [CA5394 verwenden Sie keine unsichere Zufälligkeit.](../code-quality/ca5394.md) | Die Verwendung eines kryptografisch schwachen Pseudozufallszahlen-Generators kann es einem Angreifer ermöglichen, vorherzusagen, welcher sicherheitsrelevante Wert generiert wird. |
| CA5395 | [CA5395 Miss httpVerb-Attribut für Aktionsmethoden](../code-quality/ca5395.md) | Alle Aktionsmethoden, die Daten erstellen, bearbeiten, löschen oder anderweitig ändern, müssen durch das antifälschungs Attribut von Website übergreifenden Anforderungs Fälschungs Angriffen geschützt werden. Das Ausführen eines Get-Vorgangs sollte ein sicherer Vorgang sein, der keine Nebeneffekte hat und die beibehaltenen Daten nicht ändert. |
| CA5396 | [CA5396 legen Sie HttpOnly für HttpCookie auf true fest.](../code-quality/ca5396.md) | Stellen Sie sicher, dass sicherheitsrelevante http-Cookies als "HttpOnly" gekennzeichnet sind. Dies bedeutet, dass Webbrowser das Zugreifen auf die Cookies durch Skripts nicht zulassen sollten. Injizierte schädliche Skripts sind eine gängige Methode zum stehlen von Cookies. |
| CA5399 | [CA5399 Überprüfung der httpclient-Zertifikat Sperr Liste definitiv deaktivieren](../code-quality/ca5399.md) | Ein gesperrtes Zertifikat ist nicht mehr vertrauenswürdig. Sie kann von Angreifern verwendet werden, die bei der HTTPS-Kommunikation schädliche Daten übergeben oder vertrauliche Daten stehlen. |
| CA5400 | [CA5400 stellen Sie sicher, dass die Überprüfung der httpclient-Zertifikat Sperr Liste nicht](../code-quality/ca5400.md) | Ein gesperrtes Zertifikat ist nicht mehr vertrauenswürdig. Sie kann von Angreifern verwendet werden, die bei der HTTPS-Kommunikation schädliche Daten übergeben oder vertrauliche Daten stehlen. |
| CA5401 | [CA5401 verwenden Sie nicht "" für nicht standardmäßige IV.](../code-quality/ca5401.md) | Die symmetrische Verschlüsselung sollte immer einen nicht wiederholbaren Initialisierungs Vektor verwenden, um Wörterbuchangriffe zu verhindern. |
| CA5402 | [CA5402 Verwenden von "kreateverschlüsseltor" mit dem Standard-IV](../code-quality/ca5402.md) | Die symmetrische Verschlüsselung sollte immer einen nicht wiederholbaren Initialisierungs Vektor verwenden, um Wörterbuchangriffe zu verhindern. |
