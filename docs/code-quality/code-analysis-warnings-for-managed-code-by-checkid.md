---
title: Übersicht über Codequalitätsregeln
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
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
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
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
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a298ab142ae6a44c1fb24b2cb1b752f6beb4a68e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037236"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>Regeln für die Code Qualitätsanalyse nach Regel-ID

In der folgenden Tabelle sind die Regeln zur Code Qualitätsanalyse nach Regel Bezeichner aufgeführt.

| CheckId | Warnung | BESCHREIBUNG |
|---------| - | - |
| CA1000 | [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000.md) | Wenn ein statischer Member eines generischen Typs aufgerufen wird, muss das Typargument für den Typ angegeben werden. Wenn ein generischer Instanzmember, der keine Unterstützung für Rückschlüsse bietet, aufgerufen wird, muss das Typargument für den Member angegeben werden. In diesen beiden Fällen ist die Syntax zum Angeben des Typarguments unterschiedlich und leicht zu verwechseln. |
| CA1001 | [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können.](../code-quality/ca1001.md) | Eine Klasse deklariert und implementiert ein Instanzenfeld, das den System.IDisposable-Typ aufweist, IDisposable jedoch nicht implementiert. Eine Klasse, die ein IDisposable-Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte die IDisposable-Schnittstelle implementieren. |
| CA1002 | [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002.md) | System. Collections. Generic. List< (of \<(T> ) >) ist eine generische Sammlung, die für Leistung und nicht Vererbung konzipiert ist. Daher enthält List keine virtuellen Member. Stattdessen sollten die generischen Auflistungen, die im Hinblick auf die Vererbung entworfen wurden, verfügbar gemacht werden. |
| CA1003 | [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003.md) |Ein Typ enthält einen Delegaten, der void zurückgibt. Die zugehörige Signatur enthält zwei Parameter (der erste ist ein Objekt, der zweite ein Typ, der EventArgs zugewiesen werden kann), und Microsoft .NET Framework 2.0 ist Ziel der enthaltenden Assembly. |
| CA1005 | [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005.md) | Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Es ist in der Regel offensichtlich mit einem Typparameter, wie in der Liste \<T> , und in bestimmten Fällen mit zwei Typparametern, wie im Wörterbuch \<TKey, TValue> . Mehr als zwei Typparameter hingegen bereiten den meisten Benutzern Schwierigkeiten. |
| CA1008 | [CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen.](../code-quality/ca1008.md) | Der Standardwert einer nicht initialisierten Enumeration ist ebenso wie der anderer Werttypen 0 (null). Eine Enumeration ohne das Flags-Attribut sollte einen Member mit dem Wert 0 (null) definieren, damit der Standardwert ein gültiger Wert der Enumeration ist. Wenn eine Enumeration, auf die FlagsAttribute angewendet wird, einen Member mit dem Wert 0 (null) definiert, sollte dieser den Namen "None" haben, um anzugeben, dass in der Enumeration keine Werte festgelegt wurden. |
| CA1010 | [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010.md) | Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Anschließend kann die Auflistung zum Auffüllen generischer Auflistungstypen verwendet werden. |
| CA1012 | [CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen.](../code-quality/ca1012.md) | Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen und Sie keine Instanzen eines abstrakten Datentyps erstellen können, ist ein abstrakter Datentyp mit einem öffentlichen Konstruktor fehlerhaft konzipiert. |
| CA1014 | [CA1014: Assemblys mit CLSCompliantAttribute markieren.](../code-quality/ca1014.md) | In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Um guten Entwurfsprinzipien gerecht zu werden, muss bei allen Assemblys die CLS-Kompatibilität mit <xref:System.CLSCompliantAttribute> explizit angegeben werden. Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel. |
| CA1016 | [CA1016: Assemblys mit AssemblyVersionAttribute markieren.](../code-quality/ca1016.md) | .NET verwendet die Versionsnummer zur eindeutigen Identifizierung einer Assembly und zum Binden an Typen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden. |
| CA1017 | [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017.md) |Das ComVisibleAttribute-Attribut bestimmt, wie COM-Clients auf verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. Die COM-Sichtbarkeit kann für die gesamte Assembly festgelegt und anschließend für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut fehlt, ist der Inhalt der Assembly für COM-Clients sichtbar. |
| CA1018 | [CA1018: Attribute mit AttributeUsageAttribute markieren.](../code-quality/ca1018.md) | Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von AttributeUsageAttribute, um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. |
| CA1019 | [CA1019: Accessoren für Attributargumente definieren.](../code-quality/ca1019.md) | Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen. |
| CA1021 | [CA1021: out-Parameter vermeiden.](../code-quality/ca1021.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen dem out-Parameter und dem ref-Parametern oft unklar. |
| CA1024 | [CA1024: Nach Möglichkeit Eigenschaften verwenden.](../code-quality/ca1024.md) | Eine öffentliche oder geschützte Methode hat einen Namen, der mit "Get" beginnt. Sie nimmt keine Parameter an und gibt einen Wert zurück, bei dem es sich nicht um ein Array handelt. Die Methode ist möglicherweise als Eigenschaft geeignet. |
| CA1027 |[CA1027: Enumerationen mit FlagsAttribute markieren.](../code-quality/ca1027.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Wenden Sie FlagsAttribute auf eine Enumeration an, wenn deren benannte Konstanten sinnvoll kombiniert werden können. |
| CA1028 | [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028.md) | Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Standardmäßig wird zum Speichern des konstanten Werts der System.Int32-Datentyp verwendet. Sie können diesen zugrunde liegenden Typ zwar ändern, in den meisten Szenarien ist dies jedoch weder notwendig noch empfehlenswert. |
| CA1030 | [CA1030: Nach Möglichkeit Ereignisse verwenden.](../code-quality/ca1030.md) |Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Wenn eine Methode auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen. |
| CA1031 | [CA1031: Allgemeine Ausnahmetypen nicht auffangen.](../code-quality/ca1031.md) | Allgemeine Ausnahmen sollten nicht abgefangen werden. Fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme in der letzten Anweisung des catch-Blocks erneut aus. |
| CA1032 |[CA1032: Standardausnahmekonstruktoren implementieren.](../code-quality/ca1032.md) | Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. |
| CA1033 | [CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.](../code-quality/ca1033.md) | Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an. |
| CA1034 | [CA1034: Geschachtelte Typen sollten nicht sichtbar sein.](../code-quality/ca1034.md) | Ein geschachtelter Typ ist ein Typ, der innerhalb des Gültigkeitsbereichs eines anderen Typs deklariert ist. Geschachtelte Typen eignen sich für die Kapselung privater Implementierungsdetails der enthaltenden Typen. Bei dieser Verwendungsart sollten geschachtelte Typen nicht extern sichtbar sein. |
| CA1036 | [CA1036: Methoden bei vergleichbaren Typen überschreiben.](../code-quality/ca1036.md) |Ein öffentlicher oder geschützter Typ implementiert die System.IComparable-Schnittstelle. Er überschreibt Object.Equals nicht und überlädt auch nicht den sprachspezifischen Operator für gleich, ungleich, kleiner als und größer als. |
| CA1040 |[CA1040: Leere Schnittstellen vermeiden.](../code-quality/ca1040.md) | Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Daher definiert sie keinen Vertrag, der implementiert werden kann. |
| CA1041 | [CA1041: ObsoleteAttribute-Meldung bereitstellen.](../code-quality/ca1041.md) | Ein Typ oder Member wird mit einem System.ObsoleteAttribute-Attribut markiert, dessen ObsoleteAttribute.Message-Eigenschaft nicht angegeben wurde. Wenn ein mit ObsoleteAttribute markierter Typ oder Member kompiliert wird, wird die Message-Eigenschaft des Attributs angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. |
| CA1043 | [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.](../code-quality/ca1043.md) | Indexer (d. h. indizierte Eigenschaften) sollten ganzzahlige Typen oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. R. zum Indizieren von Datenstrukturen verwendet und erweitern den Einsatzbereich der Bibliothek. Die Verwendung des Object-Typs sollte auf die Fälle beschränkt werden, in denen der spezielle integrale oder Zeichenfolgentyp zur Entwurfszeit nicht angegeben werden kann. |
| CA1044 | [CA1044: Eigenschaften sollten nicht lesegeschützt sein.](../code-quality/ca1044.md) | Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Wenn ein Benutzer einen Wert festlegen kann, bietet es keinerlei Sicherheitsvorteile, das Lesen und Anzeigen des Werts durch den Benutzer zu sperren. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird. |
| CA1045 |[CA1045: Typen nicht als Verweis übergeben.](../code-quality/ca1045.md) | Die Übergabe von Typen als Verweis (mit out oder ref) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten. Bibliotheks Architekten, die für eine allgemeine Zielgruppe entwerfen, sollten nicht erwarten, dass Benutzer die Arbeit mit- `out` oder- `ref` Parametern meistern. |
| CA1046 | [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046.md) | Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen. |
| CA1047 |[CA1047: Geschützte Member in versiegelten Typen nicht deklarieren.](../code-quality/ca1047.md) | Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können. Per Definition kann von versiegelten Typen nicht geerbt werden. Dies bedeutet, dass geschützte Methoden für versiegelte Typen nicht aufgerufen werden können. |
| CA1050 | [CA1050: Typen in Namespaces deklarieren.](../code-quality/ca1050.md) | Typen werden in Namespaces deklariert, um Namenskonflikte zu verhindern und um verwandte Typen in einer Objekthierarchie zu organisieren. |
| CA1051 | [CA1051: Sichtbare Instanzfelder nicht deklarieren.](../code-quality/ca1051.md) | Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder sollten privat oder intern sein und durch die Verwendung von Eigenschaften verfügbar gemacht werden. |
| CA1052 | [CA1052: Statische Haltertypen sollten versiegelt sein.](../code-quality/ca1052.md) | Ein öffentlicher oder geschützter Typ enthält nur statische Member und wird nicht mit dem sealed (C#-Referenz)-Modifizierer (NotInheritable) deklariert. Ein Typ, der nicht geerbt werden soll, sollte mit dem sealed-Modifizierer markiert werden, um seine Verwendung als Basistyp zu verhindern. |
| CA1053 |[CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053.md) | Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor. Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Die Zeichenfolgenüberladung sollte die URI-Überladung aus Sicherheitsgründen mit dem Zeichenfolgenargument aufrufen. |
| CA1054 | [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054.md) | Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, sollte eine entsprechende Überladung angegeben werden, die eine Instanz der URI-Klasse annimmt, die diese Dienste auf sichere Weise bereitstellt. |
| CA1055 | [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055.md) | Diese Regel geht davon aus, dass die Methode einen URI zurückgibt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1056 | [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056.md) | Diese Regel geht davon aus, dass die Eigenschaft einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die System.Uri-Klasse stellt diese Dienste auf sichere Weise bereit. |
| CA1058 | [CA1058: Typen sollten bestimmte Basistypen nicht erweitern.](../code-quality/ca1058.md) | Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Verwenden Sie eine der Alternativen. |
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
| CA1303 | [CA1303: Literale nicht als lokalisierte Parameter übergeben.](../code-quality/ca1303.md) | Eine extern sichtbare Methode übergibt ein Zeichenfolgenliteralzeichen als Parameter an einen .net-Konstruktor oder eine Methode, und diese Zeichenfolge muss lokalisierbar sein. |
| CA1304 | [CA1304: CultureInfo angeben.](../code-quality/ca1304.md) | Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen System.Globalization.CultureInfo-Parameter akzeptiert. Die Methode oder der Konstruktor ruft nicht die Überladung auf, die den CultureInfo-Parameter akzeptiert. Wenn ein CultureInfo-Objekt oder ein System.IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1305 | [CA1305: IFormatProvider angeben.](../code-quality/ca1305.md) | Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen System.IFormatProvider-Parameter akzeptieren; die Methode oder der Konstruktor ruft die Überladung nicht auf, die den IFormatProvider-Parameter akzeptiert. Wenn ein System.Globalization.CultureInfo-Objekt oder ein IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt. |
| CA1307 | [CA1307: "StringComparison" zur Verdeutlichung angeben](../code-quality/ca1307.md) | Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein StringComparison-Parameter festgelegt wird. |
| CA1308 |[CA1308: Zeichenfolgen in Großbuchstaben normalisieren.](../code-quality/ca1308.md) | Zeichenfolgen sollten in Großschreibung normalisiert werden. Für eine kleine Gruppe von Zeichen wird bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt. |
| CA1309 | [CA1309: Ordinal-StringComparison verwenden.](../code-quality/ca1309.md) | Durch einen nicht linguistischen Zeichenfolgenvergleich wird der StringComparison-Parameter nicht auf Ordinal und nicht auf OrdinalIgnoreCase festgelegt. Wenn der Parameter explizit auf StringComparison.Ordinal oder StringComparison.OrdinalIgnoreCase festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert. |
| CA1310 | [CA1310: "StringComparison" für Richtigkeit angeben](../code-quality/ca1310.md) | Eine Zeichen folgen Vergleichsoperation verwendet eine Methoden Überladung, die keinen StringComparison-Parameter festgelegt und standardmäßig einen kulturspezifischen Zeichen folgen Vergleich verwendet. |
| CA1401 | [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401.md) | Eine öffentliche oder geschützte Methode in einem öffentlichen Typ enthält das System.Runtime.InteropServices.DllImportAttribute-Attribut (in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] auch durch das Declare-Schlüsselwort implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| CA1417 | [CA1417: nicht `OutAttribute` für Zeichen folgen Parameter für P/Aufrufe verwenden](../code-quality/ca1417.md) | Zeichen folgen Parameter, die mit dem als Wert übermittelt werden, `OutAttribute` können die Laufzeit destabilisieren, wenn die Zeichenfolge eine Internpool vorhanden Zeichenfolge ist. |
| CA1501 | [CA1501: Übermäßige Vererbung vermeiden.](../code-quality/ca1501.md) | Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. |
| CA1502 | [CA1502: Übermäßige Komplexität vermeiden.](../code-quality/ca1502.md) | Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird. |
| CA1505 | [CA1505: Nicht wartbaren Code vermeiden.](../code-quality/ca1505.md) | Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre. |
| CA1506 | [CA1506: Übermäßige Klassenkopplungen vermeiden.](../code-quality/ca1506.md) | Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden. |
| CA1507 | [CA1507: „nameof“ anstelle der Zeichenfolge verwenden](../code-quality/ca1507.md) | Ein Zeichenfolgenliterals wird als Argument verwendet, bei dem ein- `nameof` Ausdruck verwendet werden kann. |
| CA1508 | [CA1508: Toten Bedingungscode vermeiden](../code-quality/ca1508.md) | Eine Methode verfügt über bedingten Code, der immer zu oder zur Laufzeit ausgewertet wird `true` `false` . Dies führt zu einem unzustellbaren Code in der `false` Verzweigung der Bedingung. |
| CA1509 | [CA1509: Ungültiger Eintrag in der Konfigurationsdatei für die Codemetrik.](../code-quality/ca1509.md) | Code metrikregeln, wie z. b. [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) und [CA1506](ca1506.md), haben eine Konfigurationsdatei mit dem Namen mit `CodeMetricsConfig.txt` einem ungültigen Eintrag bereitgestellt. |
| CA1700 | [CA1700: Enumerationswerte nicht mit "Reserviert" benennen.](../code-quality/ca1700.md) | Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. |
| CA1707 | [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707.md) | Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft. |
| CA1708 | [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708.md) | Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen. |
| CA1710 | [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.](../code-quality/ca1710.md) |Die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen weisen stets ein Suffix auf, das mit dem Basistyp oder der Schnittstelle verknüpft ist. |
| CA1711 | [CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711.md) | Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden. |
| CA1712 | [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.](../code-quality/ca1712.md) | Den Namen von Enumerationsmembern wird der Typname nicht als Präfix vorangestellt, da die Typinformationen von den Entwicklungswerkzeugen bereitgestellt werden sollten. |
| CA1713 | [CA1713: Ereignisse sollten kein Before- oder After-Präfix aufweisen.](../code-quality/ca1713.md) | Der Name eines Ereignisses beginnt mit "Before" oder "After". Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben. |
| CA1714 | [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714.md) | Eine öffentliche Enumeration verfügt über das System.FlagsAttribute-Attribut, und der Name endet nicht in der Pluralform ("s"). Die Namen von mit FlagsAttribute markierten Typen stehen im Plural, da das Attribut angibt, dass mehr als ein Wert festgelegt werden kann. |
| CA1715 | [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.](../code-quality/ca1715.md) | Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem großen "I". Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit einem großen "T". |
| CA1716 | [CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.](../code-quality/ca1716.md) | Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein. Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind. |
| CA1717 | [CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1717.md) | Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können. |
| CA1720 |[CA1720: Bezeichner dürfen keine Typnamen enthalten.](../code-quality/ca1720.md) | Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen. |
| CA1721 | [CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.](../code-quality/ca1721.md) |Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get"-Methoden und -Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen. |
| CA1724 | [CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.](../code-quality/ca1724.md) | Typnamen sollten nicht mit den Namen von .NET-Namespaces identisch sein. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden. |
| CA1725 | [CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen.](../code-quality/ca1725.md) | Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt. |
| CA1801 | [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801.md) | Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. |
| CA1802 |[CA1802: Nach Möglichkeit Literale verwenden.](../code-quality/ca1802.md) |Ein Feld wird als static und read-only deklariert (Shared und ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) und mit einem Wert initialisiert, der zur Kompilierungszeit berechnet werden kann. Da der Wert, der dem Zielfeld zugewiesen ist, zur Kompilierzeit komprimiert werden kann, ändern Sie die Deklaration in ein Konstantenfeld (Konstanten in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), sodass der Wert zur Kompilierzeit anstelle der Laufzeit berechnet wird. |
| CA1805 | [CA1805: Keine unnötige Initialisierung.](../code-quality/ca1805.md) | Die .NET-Laufzeit initialisiert alle Felder von Verweis Typen mit ihren Standardwerten, bevor der Konstruktor ausgeführt wird. In den meisten Fällen ist das explizite Initialisieren eines Felds auf seinen Standardwert redundant, wodurch Wartungskosten erhöht und die Leistung beeinträchtigt werden kann (z. b. mit erhöhter assemblygröße). |
| CA1806 | [CA1806: Methodenergebnisse nicht ignorieren.](../code-quality/ca1806.md) | Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM-Methode oder P/Invoke-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird. |
| CA1810 | [CA1810: Statische Felder von Referenztypen inline initialisieren.](../code-quality/ca1810.md) | Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. |
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
| CA1826 |[CA1826: Eigenschaft anstelle der LINQ-Enumerable-Methode verwenden.](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> Die LINQ-Methode wurde für einen Typ verwendet, der eine äquivalente, effizientere Eigenschaft unterstützt. |
| CA1827 |[CA1827: Count/LongCount nicht verwenden, wenn Any verwendet werden kann.](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> die-Methode oder die- <xref:System.Linq.Enumerable.LongCount%2A> Methode wurde verwendet, wenn die <xref:System.Linq.Enumerable.Any%2A> Methode effizienter wäre. |
| CA1828 |[CA1828: CountAsync/LongCountAsync nicht verwenden, wenn AnyAsync verwendet werden kann.](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> die-Methode oder die- <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> Methode wurde verwendet, wenn die <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> Methode effizienter wäre. |
| CA1829 |[CA1829: Length/Count-Eigenschaft anstelle der Enumerable.Count-Methode verwenden.](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> Die LINQ-Methode wurde für einen Typ verwendet, der eine äquivalente, effizientere oder-Eigenschaft unterstützt `Length` `Count` . |
| CA1830 |[CA1830: Bevorzugen Sie stark typisierte Append- und Insert-Methodenüberladungen für StringBuilder.](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> und <xref:System.Text.StringBuilder.Insert%2A> Stellen über Ladungen für mehrere Typen über bereit <xref:System.String> .  Bevorzugen Sie nach Möglichkeit die stark typisierten über Ladungen über die Verwendung von ToString () und der Zeichen folgen basierten Überladung. |
| CA1831 |[CA1831: Verwenden Sie für Zeichenfolgen bei Bedarf anstelle von Range-basierten Indexern „AsSpan“.](../code-quality/ca1831.md) | Wenn Sie einen Range-Indexer für eine Zeichenfolge verwenden und den Wert dem Typ "Read onlyspan char" implizit zuweisen &lt; &gt; , wird die-Methode <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils der Zeichenfolge erzeugt wird. |
| CA1832 |[CA1832: Verwenden Sie „AsSpan“ oder „AsMemory“ anstelle von Range-basierten Indexern zum Abrufen eines ReadOnlySpan- oder ReadOnlyMemory-Teils eines Arrays.](../code-quality/ca1832.md) | Wenn Sie einen Range-Indexer für ein Array verwenden und den Wert implizit einem- <xref:System.ReadOnlySpan%601> oder- <xref:System.ReadOnlyMemory%601> Typ zuweisen, wird die-Methode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils des Arrays erzeugt wird. |
| CA1833 |[CA1833: Verwenden Sie „AsSpan“ oder „AsMemory“ anstelle von Range-basierten Indexern zum Abrufen eines Span- oder Memory-Teils eines Arrays.](../code-quality/ca1833.md) | Wenn Sie einen Range-Indexer für ein Array verwenden und den Wert implizit einem- <xref:System.Span%601> oder- <xref:System.Memory%601> Typ zuweisen, wird die-Methode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> anstelle von verwendet <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , wodurch eine Kopie des angeforderten Teils des Arrays erzeugt wird. |
| CA1834 |[CA1834: Verwenden von StringBuilder.Append(char) für Zeichenfolgen mit einem einzelnen Zeichen](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> verfügt über eine-Überladung `Append` , die einen `char` als sein Argument annimmt. Bevorzugen Sie die `char` Überladung aus Leistungsgründen. |
| CA1835 |[CA1835: bevorzugen Sie die "Memory"-basierten über Ladungen für "Read Async" und "schreiteasync".](../code-quality/ca1835.md) | ' Stream ' weist eine ' Schreib async '-Überladung auf, die ein ' Memory &lt; Byte &gt; ' als erstes Argument annimmt, und eine ' schreiteasync '-Überladung, die ein ' Read onlymemory &lt; Byte &gt; ' als erstes Argument annimmt. Bevorzugen Sie das Aufrufen der Speicher basierten über Ladungen, die effizienter sind. |
| CA1836 |[CA1836: bevorzugen `IsEmpty` , `Count` Wenn verfügbar](../code-quality/ca1836.md) | Bevorzugt eine `IsEmpty` Eigenschaft, die effizienter ist als `Count` , oder, `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> um zu bestimmen, ob das Objekt Elemente enthält oder nicht. |
| CA1837 | [CA1837: Verwenden Sie `Environment.ProcessId` anstelle von. `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` ist einfacher und schneller als `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: `StringBuilder` Parameter für P/Aufrufe vermeiden](../code-quality/ca1838.md) | Beim Marshalling von "StringBuilder" wird immer eine native Puffer Kopie erstellt, was zu mehreren Zuordnungen für einen marshallingvorgang führt. |
| CA2000 | [CA2000: Objekte verwerfen, bevor Bereich verloren geht.](../code-quality/ca2000.md) | Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden. |
| CA2002 |[CA2002: Auf Objekten mit schwacher Identität nicht sperren.](../code-quality/ca2002.md) |Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt. |
| CA2007 | [CA2007: Eine Aufgabe nicht direkt abwarten](ca2007.md) | Eine asynchrone Methode [erwartet](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> direkt ein. Wenn eine asynchrone Methode <xref:System.Threading.Tasks.Task> direkt auf einen wartet, erfolgt die Fortsetzung in dem Thread, der die Aufgabe erstellt hat. Dieses Verhalten kann sich in Bezug auf die Leistung als kostspielig erweisen und kann zu einem Deadlock im UI-Thread führen. Rufen <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> Sie auf, um ihre Absicht für die Fortsetzung zu signalisieren. |
| CA2008 | [CA2008: Keine Tasks ohne Übergabe eines TaskSchedulers erstellen](ca2008.md) | Ein Task Erstellungs-oder Fortsetzungs Vorgang verwendet eine Methoden Überladung, die keinen <xref:System.Threading.Tasks.TaskScheduler> Parameter angibt. |
| CA2009 | [CA2009: „ToImmutableCollection“ nicht für einen ImmutableCollection-Wert aufrufen.](ca2009.md) | `ToImmutable` die Methode wurde für eine unveränderliche Auflistung aus dem <xref:System.Collections.Immutable> Namespace unnötig aufgerufen. |
| CA2011 | [CA2011: Eigenschaft nicht innerhalb ihres Setters zuweisen](ca2011.md) | Einer Eigenschaft wurde versehentlich ein Wert innerhalb ihrer eigenen [Set-Zugriffs](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)Methode zugewiesen. |
| CA2012 | [CA2012: Verwenden Sie ValueTasks ordnungsgemäß.](ca2012.md) | Valuetasks, die von Element aufrufen zurückgegeben wurden, sollen direkt gewartet werden.  Versucht, eine valuetask mehrmals zu verwenden oder direkt auf das Ergebnis zuzugreifen, bevor es als abgeschlossen bezeichnet wird, kann zu einer Ausnahme oder Beschädigung führen.  Das ignorieren einer solchen valuetask ist wahrscheinlich ein Hinweis auf einen Funktionsfehler und kann die Leistung beeinträchtigen. |
| CA2013 | [CA2013: Verwenden Sie ReferenceEquals nicht mit Werttypen.](ca2013.md) | Beim Vergleichen von Werten mit werden bei <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA und objB Werttypen verwendet, bevor Sie an die-Methode übermittelt werden <xref:System.Object.ReferenceEquals%2A> . Dies bedeutet, dass auch dann, wenn objA und objB dieselbe Instanz eines Werttyps darstellen, die <xref:System.Object.ReferenceEquals%2A> Methode trotzdem false zurückgibt. |
| CA2014 | [CA2014: Verwenden Sie stackzuweisung nicht in Schleifen.](ca2014.md) | Der von stackzugewiesc zugewiesene Stapel Speicher wird nur am Ende des Aufruf der aktuellen Methode freigegeben.  Die Verwendung in einer-Schleife kann zu unbegrenzten Stapel Vergrößerung und letztlichen Stapelüberlauf Bedingungen führen. |
| CA2015 | [CA2015: Finalizer nicht für Typen definieren, die von memorymanager &lt; T abgeleitet sind&gt;](ca2015.md) | Durch das Hinzufügen eines Finalizers zu einem von abgeleiteten Typ <xref:System.Buffers.MemoryManager%601> kann der Speicher freigegeben werden, während er noch von einem verwendet wird <xref:System.Span%601> . |
| CA2016 | [CA2016: Parameter "CancellationToken" an Methoden weiterleiten, die diesen Parameter akzeptieren.](ca2016.md) | Leiten Sie den- `CancellationToken` Parameter an Methoden weiter, die einen annehmen, um sicherzustellen, dass die Vorgangs Abbruch Benachrichtigungen ordnungsgemäß weitergegeben werden, oder übergeben Sie `CancellationToken.None` explizit, um anzugeben, dass das Token absichtlich nicht |
| CA2100 | [CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen.](../code-quality/ca2100.md) | Eine Methode legt die System.Data.IDbCommand.CommandText-Eigenschaft mithilfe einer Zeichenfolge fest, die aus einem Zeichenfolgenargument für die Methode erstellt wird. Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. |
| CA2101 |[CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101.md) | Ein Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling der Zeichenfolge durch. Auf diese Weise kann potenziell eine Sicherheitslücke verursacht werden. |
| CA2109 | [CA2109: Sichtbare Ereignishandler überprüfen.](../code-quality/ca2109.md) | Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt. Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist. |
| CA2119 | [CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.](../code-quality/ca2119.md) | Ein vererbbarer öffentlicher Typ stellt eine überschreibbare Methodenimplementierung einer internen Schnittstelle (Friend in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) bereit. Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird. |
| CA2153 |[CA2153: Vermeiden der Behandlung von beschädigten Zustands Ausnahmen](../code-quality/ca2153.md) | Beschädigte Zustands Ausnahmen (CSES) weisen darauf hin, dass im Prozess Speicher Beschädigungen vorhanden sind. Diese abzufangen, statt einen Absturz des Prozesses zuzulassen, führt zu Sicherheitsrisiken, falls ein Angreifer einen Exploit in den beschädigten Speicherbereich einschleusen kann. |
| CA2200 | [CA2200: Erneut ausführen, um Stapeldetails beizubehalten.](../code-quality/ca2200.md) | Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren. |
| CA2201 | [CA2201: Keine reservierten Ausnahmetypen auslösen.](../code-quality/ca2201.md) | Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2207 | [CA2207: Statische Felder für Werttyp inline initialisieren.](../code-quality/ca2207.md) | Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor. |
| CA2208 |[CA2208: Argumentausnahmen korrekt instanziieren.](../code-quality/ca2208.md) | Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird. |
| CA2211 |[CA2211: Nicht konstante Felder sollten nicht sichtbar sein.](../code-quality/ca2211.md) | Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Der Zugriff auf ein solches Feld muss sorgfältig kontrolliert werden und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt. |
| CA2213 | [CA2213: Verwerfbare Felder verwerfen.](../code-quality/ca2213.md) | Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen. |
| CA2214 | [CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.](../code-quality/ca2214.md) | Wenn ein Konstruktor eine virtuelle Methode aufruft, wurde möglicherweise der Konstruktor für die Instanz, von der die Methode aufgerufen wird, nicht ausgeführt. |
| CA2215 | [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.](../code-quality/ca2215.md) | Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden. |
| CA2216 |[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.](../code-quality/ca2216.md) | Ein Typ, der System.IDisposable implementiert und Felder besitzt, bei denen die Verwendung nicht verwalteter Ressourcen empfohlen wird, implementiert keinen Finalizer wie von Object.Finalize beschrieben. |
| CA2217 | [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217.md) |Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und weist einen oder mehrere Werte auf, die keine Potenzen von 2 und keine Kombination von anderen in der Enumeration definierten Werten bilden. |
| CA2219 | [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.](../code-quality/ca2219.md) | Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen. |
| CA2225 | [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225.md) |Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternativmember gewährt auf die gleiche Funktionalität wie der Operator Zugriff und wird für Entwickler bereitgestellt, die in Sprachen programmieren, in denen überladene Operatoren nicht unterstützt werden. |
| CA2226 | [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226.md) | Ein Typ implementiert den Gleichheits- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren. |
| CA2227 |[CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.](../code-quality/ca2227.md) |Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. |
| CA2229 | [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229.md) | Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor. |
| CA2231 | [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231.md) | Ein Werttyp überschreibt Object.Equals, implementiert jedoch nicht den Gleichheitsoperator. |
| CA2234 | [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234.md) | Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält. Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt. |
| CA2235 | [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235.md) | Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert. |
| CA2237 | [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237.md) | Damit Typen von der Common Language Runtime als serialisierbar erkannt werden, müssen sie mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der ISerializable-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet. |
| CA2241 | [CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.](../code-quality/ca2241.md) | Das an System.String.Format übergebene format-Argument enthält keine Formatelemente, die den einzelnen Objektargumenten entsprechen oder umgekehrt. |
| CA2242 |[CA2242: Ordnungsgemäß auf NaN testen.](../code-quality/ca2242.md) | Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double). |
| CA2243 |[CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.](../code-quality/ca2243.md) | Der Zeichenfolgenliteral-Parameter eines Attributs wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert. |
| CA2244 | [CA2244: Keine Initialisierungen indizierter Elemente duplizieren](../code-quality/ca2244.md) | Ein Objektinitialisierer verfügt über mehr als einen indizierten Elementinitialisierer mit demselben Konstanten Index. Alle außer der letzte Initialisierer sind redundant. |
| CA2245 | [CA2245: Keine Zuweisung einer Eigenschaft zu sich selbst](../code-quality/ca2245.md) | Eine Eigenschaft wurde versehentlich selbst zugewiesen. |
| CA2246 | [CA2246: Keine Zuweisung eines Symbols und seines Members in der gleichen Anweisung](../code-quality/ca2246.md) | Es wird nicht empfohlen, ein Symbol und dessen Member, d. h. ein Feld oder eine Eigenschaft, in derselben Anweisung zuzuweisen. Es ist nicht klar, ob der Element Zugriff dazu gedacht war, den alten Wert des Symbols vor der Zuweisung oder den neuen Wert aus der Zuweisung in dieser Anweisung zu verwenden. |
| CA2247 | [CA2247: das Argument, das an den TaskCompletionSource-Konstruktor übergeben wurde, sollte eine taskupationoptions-Enumeration anstelle der TaskContinuationOptions-Enumeration sein.](../code-quality/ca2247.md) | TaskCompletionSource verfügt über Konstruktoren, die taskkreationoptions verwenden, die die zugrunde liegende Aufgabe steuern, und Konstruktoren, die den Objektzustand annehmen, der in der Aufgabe gespeichert ist.  Das versehentliche übergeben von TaskContinuationOptions anstelle von taskkreationoptions führt dazu, dass der Aufruf die Optionen als Zustand behandelt. |
| CA2248 | [CA2248: Geben Sie das richtige enum-Argument für „Enum.HasFlag“ an.](../code-quality/ca2248.md) | Der als Argument an den `HasFlag` Methodenaufruf umgegebene Aufzählungs Typ unterscheidet sich vom aufrufenden Aufzählungs Typen. |
| CA2249 | [CA2249: Erwägen Sie die Verwendung von "String.Contains" anstelle von "String.IndexOf"](../code-quality/ca2249.md) | Aufrufe `string.IndexOf` von, bei denen das Ergebnis verwendet wird, um zu überprüfen, ob eine Teil Zeichenfolge vorhanden oder nicht vorhanden ist, können durch ersetzt werden `string.Contains` . |
| CA2300 | [CA2300: Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden](../code-quality/ca2300.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2301 | [CA2301: BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen](../code-quality/ca2301.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2302 | [CA2302: Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen](../code-quality/ca2302.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2305 | [CA2305: Unsicheren Deserialisierer nicht verwenden: LosFormatter](../code-quality/ca2305.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2310 | [CA2310: Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer](../code-quality/ca2310.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2311 | [CA2311: Nicht deserialisieren, ohne zuerst NetDataContractSerializer.Binder festzulegen](../code-quality/ca2311.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2312 | [CA2312: Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist](../code-quality/ca2312.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2315 | [CA2315: Unsicheren Deserialisierer nicht verwenden: ObjectStateFormatter](../code-quality/ca2315.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2321 | [CA2321: Nicht mit JavaScriptSerializer und SimpleTypeResolver deserialisieren](../code-quality/ca2321.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2322 | [CA2322: Vor dem Deserialisieren sicherstellen, dass JavaScriptSerializer nicht mit SimpleTypeResolver initialisiert ist](../code-quality/ca2322.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2326 | [CA2326: Keine anderen TypeNameHandling-Werte als None (Keine) verwenden](../code-quality/ca2326.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2327 | [CA2327: Keine unsichere JsonSerializerSettings-Klasse verwenden](../code-quality/ca2327.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2328 | [CA2328: Sicherstellen, dass JsonSerializerSettings sicher ist](../code-quality/ca2328.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2329 | [CA2329: Nicht mit JsonSerializer mit unsicherer Konfiguration deserialisieren](../code-quality/ca2329.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2330 | [CA2330: Sicherstellen, dass JsonSerializer eine sichere Konfiguration bei der Deserialisierung verwendet](../code-quality/ca2330.md) | Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. |
| CA2350 | [CA2350: Sicherstellen, dass die Eingabe von DataTable.ReadXml() vertrauenswürdig ist](ca2350.md) | Beim Deserialisieren eines <xref:System.Data.DataTable> mit nicht vertrauenswürdiger Eingabe kann ein Angreifer böswillige Eingaben erstellen, um einen Denial-of-Service-Angriff auszuführen. Möglicherweise gibt es unbekannte Sicherheitsrisiken bei der Remote Codeausführung. |
| CA2351 | [CA2351: Sicherstellen, dass die Eingabe von DataSet.ReadXml() vertrauenswürdig ist](ca2351.md) | Beim Deserialisieren eines <xref:System.Data.DataSet> mit nicht vertrauenswürdiger Eingabe kann ein Angreifer böswillige Eingaben erstellen, um einen Denial-of-Service-Angriff auszuführen. Möglicherweise gibt es unbekannte Sicherheitsrisiken bei der Remote Codeausführung. |
| CA2352 | [CA2352: Unsichere DataSet- oder DataTable-Elemente in einem serialisierbaren Typ können anfällig für Angriffe durch Remotecodeausführung sein](ca2352.md) | Eine mit markierte Klasse oder Struktur <xref:System.SerializableAttribute> enthält ein <xref:System.Data.DataSet> <xref:System.Data.DataTable> -oder-Feld oder eine-Eigenschaft und verfügt nicht über eine <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Unsichere DataSet- oder DataTable-Elemente in einem serialisierbaren Typ](ca2353.md) | Eine Klasse oder Struktur, die mit einem XML-serialisierungsattribut oder einem Daten Vertrags Attribut gekennzeichnet ist, enthält ein- <xref:System.Data.DataSet> <xref:System.Data.DataTable> Feld oder eine-Eigenschaft. |
| CA2354 | [CA2354: Unsichere DataSet- oder DataTable-Elemente in einem deserialisierten Objektgraph können anfällig für Angriffe durch Remotecodeausführung sein](ca2354.md) | Die Deserialisierung mit einem <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> serialisierten und das Objekt Diagramm des umgewandelt Type kann ein-oder-Objekt enthalten <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Unsichere DataSet- oder DataTable-Elemente in einem deserialisierten Objektgraph](ca2355.md) | Deserialisierung, wenn das Objekt Diagramm des eingefügten oder des angegebenen Typs ein oder ein enthalten kann <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: unsicheres DataSet oder Datentabelle im webdeserialisierten Objekt Diagramm](ca2356.md) | Eine Methode mit einem <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> oder <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> weist einen Parameter auf, der auf <xref:System.Data.DataSet> oder verweisen kann <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: Sicherstellen, dass die automatisch generierte Klasse mit DataSet.ReadXml() nicht mit nicht vertrauenswürdigen Daten verwendet wird](ca2361.md) | Beim Deserialisieren eines <xref:System.Data.DataSet> mit nicht vertrauenswürdiger Eingabe kann ein Angreifer böswillige Eingaben erstellen, um einen Denial-of-Service-Angriff auszuführen. Möglicherweise gibt es unbekannte Sicherheitsrisiken bei der Remote Codeausführung. |
| CA2362 | [CA2362: Ein unsicheres DataSet- oder DataTable-Element in einem automatisch generierten, serialisierbaren Typ kann für Angriffe durch Remotecodeausführung anfällig sein](ca2362.md) | Wenn nicht vertrauenswürdige Eingaben mit <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> deserialisiert werden und das deserialisierte Objekt Diagramm ein-oder-Objekt enthält <xref:System.Data.DataSet> <xref:System.Data.DataTable> , kann ein Angreifer eine schädliche Nutzlast erstellen, um einen Remote Code Ausführungs Angriff auszuführen. |
| CA3001 | [CA3001: Review code for SQL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von SQL-Befehlen)](../code-quality/ca3001.md) | Beachten Sie beim Arbeiten mit nicht vertrauenswürdigen Eingabe-und SQL-Befehlen, dass SQL-Injection-Angriffe berücksichtigt werden. Ein SQL Injection-Angriff kann bösartige SQL-Befehle ausführen und so die Sicherheit und Integrität Ihrer Anwendung beeinträchtigen. |
| CA3002 | [CA3002: Review code for XSS vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch XSS)](../code-quality/ca3002.md) | Beachten Sie beim Arbeiten mit nicht vertrauenswürdigen Eingaben aus Webanforderungen, dass XSS-Angriffe (Cross-Site Scripting) berücksichtigt werden. Ein XSS-Angriff fügt nicht vertrauenswürdige Eingaben in die unformatierte HTML-Ausgabe ein, sodass der Angreifer bösartige Skripts ausführen oder den Inhalt auf der Webseite in böswilliger Absicht ändern kann. |
| CA3003 | [CA3003: Review code for file path injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen über einen Dateipfad)](../code-quality/ca3003.md) | Wenn Sie mit nicht vertrauenswürdigen Eingaben aus Webanforderungen arbeiten, achten Sie darauf, benutzergesteuerte Eingaben beim Angeben von Pfaden zu Dateien zu verwenden. |
| CA3004 | [CA3004: Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)](../code-quality/ca3004.md) | Die Offenlegung von Ausnahme Informationen bietet Angreifern Einblicke in die internale Ihrer Anwendung, die Angreifern bei der Suche nach anderen Sicherheitsrisiken helfen können. |
| CA3006 | [CA3006: Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)](../code-quality/ca3006.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben, dass Befehls Injection-Angriffe berücksichtigt werden. Ein Befehl zum Einschleusen von Befehlen kann bösartige Befehle auf dem zugrunde liegenden Betriebssystem ausführen und so die Sicherheit und Integrität des Servers beeinträchtigen. |
| CA3007 | [CA3007: Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)](../code-quality/ca3007.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben die Sicherheitsrisiken offener Umleitung. Ein Angreifer kann eine offene Umleitungs Anfälligkeit ausnutzen, um die Darstellung einer legitimen URL mithilfe Ihrer Website zu versehen, aber einen nicht ahnenden Besucher an eine phishingwebseite oder eine andere böswillige Webseite umzuleiten. |
| CA3008 | [CA3008: Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)](../code-quality/ca3008.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben die XPath-Injection-Angriffe. Das Erstellen von XPath-Abfragen mithilfe nicht vertrauenswürdiger Eingaben kann es einem Angreifer ermöglichen, die Abfrage bösartig zu manipulieren, um ein unbeabsichtigtes Ergebnis zurückzugeben, und möglicherweise den Inhalt der abgefragten XML-Daten offenzulegen. |
| CA3009 | [CA3009: Review code for XML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XML-Befehlen)](../code-quality/ca3009.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben, dass XML-Injection-Angriffe berücksichtigt werden. |
| CA3010 | [CA3010: Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)](../code-quality/ca3010.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben XAML Injection-Angriffe. XAML ist eine Markupsprache, die Objektinstanziierung und -ausführung direkt darstellt. Dies bedeutet, dass in XAML erstellte Elemente mit Systemressourcen interagieren können (z. b. Netzwerk Zugriff und Dateisystem-e/a). |
| CA3011 | [CA3011: Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)](../code-quality/ca3011.md) | Wenn Sie mit nicht vertrauenswürdigen Eingaben arbeiten, achten Sie darauf, nicht vertrauenswürdigen Code zu laden. Wenn Ihre Webanwendung nicht vertrauenswürdigen Code lädt, kann ein Angreifer möglicherweise böswillige DLLs in Ihren Prozess einfügen und bösartigen Code ausführen. |
| CA3012 | [CA3012: Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)](../code-quality/ca3012.md) | Beachten Sie bei der Arbeit mit nicht vertrauenswürdigen Eingaben die Regex Injection-Angriffe. Ein Angreifer kann eine Regex-Injektion verwenden, um einen regulären Ausdruck in böswilliger Weise zu ändern, damit der Regex unbeabsichtigte Ergebnisse findet oder der Regex übermäßige CPU beansprucht, was zu einem Denial-of-Service-Angriff führt. |
| CA3061 | [CA3061: Fügen Sie kein Schema nach URL hinzu.](../code-quality/ca3061.md) | Verwenden Sie die unsichere Überladung der Add-Methode nicht, da Sie gefährliche externe Verweise verursachen kann. |
| CA3075 | [CA3075: Unsichere DTD-Verarbeitung.](../code-quality/ca3075.md) | Wenn Sie unsichere DTDProcessing-Instanzen verwenden oder auf externe Entitätsquellen verweisen, kann der Parser unter Umständen nicht vertrauenswürdige Eingaben akzeptieren und Angreifern vertrauliche Informationen offenlegen. |
| CA3076 | [CA3076: Unsichere XSLT-Skriptausführung.](../code-quality/ca3076.md) | Wenn Sie Extensible Stylesheet Language Transformationen (XSLT) in .NET-Anwendungen unsicher ausführen, löst der Prozessor möglicherweise nicht vertrauenswürdige URI-Verweise auf, die den Angreifern vertrauliche Informationen offenlegen, was zu Denial-of-Service-und Site übergreifenden Angriffen führt. |
| CA3077 | [CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader.](../code-quality/ca3077.md) | Beim Entwerfen einer von XMLDocument und XMLTextReader abgeleiteten API sollten Sie DtdProcessing berücksichtigen. Das Verwenden unsicherer DTDProcessing-Instanzen beim Verweisen auf externe Entitätsquellen bzw. bei deren Auflösung oder das Festlegen unsicherer Werte in XML-Code kann zum Offenlegen von Informationen führen. |
| CA3147 | [CA3147: Verbhandler mit ValidateAntiForgeryToken markieren.](../code-quality/ca3147.md) | Achten Sie beim Entwerfen eines ASP.NET-MVC-Controllers auf Site übergreifende Anforderungs Fälschungs Angriffe. Mit einem Website übergreifenden Anforderungs Fälschungs Angriff können böswillige Anforderungen von einem authentifizierten Benutzer an Ihren ASP.NET MVC-Controller gesendet werden. |
| CA5350 | [CA5350: Keine schwachen Kryptografiealgorithmen verwenden.](../code-quality/ca5350.md) | Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit oder Integrität der Daten, die sie schützen, zu gewährleisten. Dieser Regel wird ausgelöst, wenn im Code TripleDES-, SHA1- oder RIPEMD160-Algorithmen gefunden werden.|
| CA5351 | [CA5351 Verwenden Sie keine unterbrochenen kryptografischen Algorithmen.](../code-quality/ca5351.md) | Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unbedingt unterbunden werden. Diese Regel wird ausgelöst, wenn der MD5-Hash-Algorithmus oder DES- bzw. RC2-Verschlüsselungsalgorithmen im Code gefunden werden. |
| CA5358 | [CA5358: Verwenden Sie keine unsicheren Verschlüsselungsmodi.](../code-quality/ca5358.md) | Verwenden Sie keine unsicheren Verschlüsselungsmodi. |
| CA5359 | [CA5359 die Zertifikats Überprüfung nicht deaktivieren](../code-quality/ca5359.md) | Ein Zertifikat kann bei der Authentifizierung der Identität des Servers helfen. Clients sollten das Serverzertifikat überprüfen, um sicherzustellen, dass Anforderungen an den vorgesehenen Server gesendet werden. Wenn servercertifikatevalidationcallback immer zurück `true` gegeben wird, übergibt jedes Zertifikat die Validierung. |
| CA5360 | [CA5360 keine gefährlichen Methoden bei der Deserialisierung aufzurufen](../code-quality/ca5360.md) | Unsichere Deserialisierung ist ein Sicherheitsrisiko, das auftritt, wenn nicht vertrauenswürdige Daten verwendet werden, um die Logik einer Anwendung zu missbrauchen, einen Denial-of-Service-Angriff (DOS) zu verursachen oder sogar beliebigen Code auszuführen, wenn Sie deserialisiert werden. Es ist oft möglich, dass böswillige Benutzer diese deserialisierungsfeatures missbrauchen, wenn die Anwendung nicht vertrauenswürdige Daten deserialisiert, die unter ihrer Kontrolle liegen. Rufen Sie insbesondere gefährliche Methoden im Prozess der Deserialisierung auf. Erfolgreiche unsichere deserialisierungsangriffe können einem Angreifer ermöglichen, Angriffe wie DOS-Angriffe, Authentifizierungs Umgehungen und Remote Codeausführung auszuführen. |
| CA5361 | [CA5361: die SChannel-Verwendung der starken Kryptografie nicht deaktivieren](../code-quality/ca5361.md) | Durch Festlegen `Switch.System.Net.DontEnableSchUseStrongCrypto` von auf `true` wird die Kryptografie für ausgehende Transport Layer Security Verbindungen (TLS) schwächer. Schwächere Kryptografie kann die Vertraulichkeit der Kommunikation zwischen Ihrer Anwendung und dem Server beeinträchtigen, sodass Angreifer die Möglichkeit erhalten, sensible Daten besser zu löschen. |
| CA5362 | [CA5362 potenzieller Verweis Cycle im deserialisierten Objekt Diagramm](../code-quality/ca5362.md) | Wenn nicht vertrauenswürdige Daten deserialisiert werden, muss jeder Code, der das deserialisierte Objekt Diagramm verarbeitet, Verweis Zyklen verarbeiten, ohne in unendliche Schleifen zu wechseln. Dies umfasst sowohl Code, der Teil eines deserialisierungsrückrufs ist, als auch Code, der das Objekt Diagramm nach Abschluss der Deserialisierung verarbeitet. Andernfalls könnte ein Angreifer einen Denial-of-Service-Angriff mit bösartigen Daten durchführen, die einen Verweis-Cycle enthalten. |
| CA5363 | [CA5363: Deaktivieren Sie die Anforderungsüberprüfung nicht.](../code-quality/ca5363.md) | Die Anforderungs Validierung ist eine Funktion in ASP.net, die HTTP-Anforderungen untersucht und bestimmt, ob Sie potenziell gefährlichen Inhalt enthalten, der zu Injection-Angriffen führen kann, einschließlich Website übergreifender Skripts. |
| CA5364 | [CA5364: Verwenden Sie keine veralteten Sicherheitsprotokolle.](../code-quality/ca5364.md) | Transport Layer Security (TLS) sichert die Kommunikation zwischen Computern, in der Regel mit HTTPS (Hypertext Transfer Protocol Secure). Ältere Protokoll Versionen von TLS sind weniger sicher als TLS 1,2 und TLS 1,3 und haben wahrscheinlich neue Sicherheitsrisiken. Vermeiden Sie ältere Protokoll Versionen, um Risiken zu minimieren. |
| CA5365 | [CA5365 HTTP-Header Überprüfung nicht deaktivieren](../code-quality/ca5365.md) | Die HTTP-Header Überprüfung ermöglicht das Codieren von Wagen Rücklauf-und Zeilenumbruch Zeichen (\r und \n), die in Antwort Headern gefunden werden. Diese Codierung kann dabei helfen, Injection-Angriffe zu vermeiden, die eine Anwendung ausnutzen, die nicht vertrauenswürdige Daten in der Kopfzeile wieder gibt. |
| CA5366 | [CA5366 XmlReader für DataSet-Lese-XML verwenden](../code-quality/ca5366.md) | Wenn Sie ein-Element <xref:System.Data.DataSet> zum Lesen von XML mit nicht vertrauenswürdigen Daten verwenden, werden möglicherweise gefährliche externe Verweise geladen, die mithilfe von <xref:System.Xml.XmlReader> mit einem sicheren Konflikt Löser oder mit deaktivierter DTD-Verarbeitung eingeschränkt werden sollten. |
| CA5367 | [CA5367 Serialisieren Sie Typen mit Zeiger Feldern nicht.](../code-quality/ca5367.md) | Diese Regel überprüft, ob eine serialisierbare Klasse mit einem Zeiger Feld oder einer Eigenschaft vorhanden ist. Member, die nicht serialisiert werden können, können ein Zeiger sein, z. b. statische Member oder Felder, die mit gekennzeichnet sind <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set viewstatueuserkey für von Seite abgeleitete Klassen](../code-quality/ca5368.md) | Das Festlegen der- <xref:System.Web.UI.Page.ViewStateUserKey> Eigenschaft kann Ihnen helfen, Angriffe auf Ihre Anwendung zu verhindern, indem Sie der Ansichts Zustandsvariablen für einzelne Benutzer einen Bezeichner zuweisen können, sodass Angreifer die Variable nicht zum Generieren eines Angriffs verwenden können. Andernfalls gibt es Sicherheitsrisiken für die Website übergreifende Anforderungs Fälschung. |
| CA5369 | [CA5369: Verwenden Sie XmlReader zur Deserialisierung.](../code-quality/ca5369.md) | Die Verarbeitung von nicht vertrauenswürdigen DTD-und XML-Schemas kann das Laden gefährlicher externer Verweise ermöglichen, das durch die Verwendung eines XmlReader mit einem sicheren Konflikt Löser oder durch deaktivierte DTD-und XML-Inline Schema Verarbeitung eingeschränkt werden sollte. |
| CA5370 | [CA5370: Verwenden Sie XmlReader als überprüfenden Reader.](../code-quality/ca5370.md) | Die Verarbeitung von nicht vertrauenswürdigen DTD-und XML-Schemas kann das Laden gefährlicher externer Verweise ermöglichen. Dieses gefährliche laden kann durch die Verwendung eines XmlReader mit einem sicheren Konflikt Löser oder durch deaktivierte DTD-und XML-Inline Schema Verarbeitung eingeschränkt werden. |
| CA5371 | [CA5371: Verwenden Sie XmlReader für Schemalesevorgänge.](../code-quality/ca5371.md) | Die Verarbeitung von nicht vertrauenswürdigen DTD-und XML-Schemas kann das Laden gefährlicher externer Verweise ermöglichen. Dies wird durch die Verwendung eines XmlReader mit einem sicheren Konflikt Löser oder mit deaktivierter DTD-und XML-Inline Schema Verarbeitung eingeschränkt. |
| CA5372 | [CA5372: Verwenden Sie XmlReader für XPathDocument.](../code-quality/ca5372.md) | Beim Verarbeiten von XML aus nicht vertrauenswürdigen Daten können gefährliche externe Verweise geladen werden, die durch die Verwendung eines XmlReader mit einem sicheren Konflikt Löser oder deaktivierter DTD-Verarbeitung eingeschränkt werden können. |
| CA5373 | [CA5373: Verwenden Sie keine veraltete Schlüsselableitungsfunktion.](../code-quality/ca5373.md) | Diese Regel erkennt den Aufruf von schwachen Schlüssel abderivations Methoden <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> und `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> ein schwacher Algorithmus PBKDF1 wurde verwendet. |
| CA5374 | [CA5374 XslTransform nicht verwenden](../code-quality/ca5374.md) | Diese Regel überprüft, ob <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> im Code instanziiert wird. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> ist mittlerweile veraltet und sollte nicht verwendet werden. |
| CA5375 | [CA5375 Shared Access Signature für Konto nicht verwenden](../code-quality/ca5375.md) | Eine Konto-SAS kann den Zugriff auf Lese-, Schreib-und Löschvorgänge für BLOB-Container, Tabellen, Warteschlangen und Dateifreigaben delegieren, die mit einer Dienst-SAS nicht zulässig sind. Es unterstützt jedoch keine Richtlinien auf Container Ebene und bietet weniger Flexibilität und Kontrolle über die gewährten Berechtigungen. Wenn böswillige Benutzer diese erhalten haben, wird Ihr Speicherkonto problemlos kompromittiert. |
| CA5376 | [CA5376 Verwenden von sharedaccessproycol httpsonly](../code-quality/ca5376.md) | Bei SAS handelt es sich um sensible Daten, die nicht als Klartext über HTTP übertragen werden können. |
| CA5377 | [CA5377 verwenden der Zugriffs Richtlinie auf Container Ebene](../code-quality/ca5377.md) | Eine Zugriffs Richtlinie auf Container Ebene kann jederzeit geändert oder widerrufen werden. Sie bietet mehr Flexibilität und Kontrolle über die gewährten Berechtigungen. |
| CA5378 | [CA5378: Deaktivieren Sie ServicePointManagerSecurityProtocols nicht.](../code-quality/ca5378.md) | Durch das Festlegen `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` von auf werden `true` die (WCF)-Transport Layer Security (WCF)-Verbindungen von Windows Communication Framework auf mithilfe von TLS 1,0 beschränkt. Diese Version von TLS wird als veraltet markiert. |
| CA5379 | [CA5379 verwenden Sie den Algorithmus für die schwache Schlüssel Ableitung nicht.](../code-quality/ca5379.md) | Die- <xref:System.Security.Cryptography.Rfc2898DeriveBytes> Klasse verwendet standardmäßig den- <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> Algorithmus. Sie sollten den Hash Algorithmus angeben, der in einigen über Ladungen des Konstruktors mit oder höher verwendet werden soll <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . Beachten Sie, dass <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> die-Eigenschaft nur über einen `get` -Accessor verfügt und keinen- `overriden` Modifizierer aufweist. |
| CA5380 | [CA5380: Fügen Sie keine Zertifikate zum Stammspeicher hinzu.](../code-quality/ca5380.md) | Diese Regel erkennt Code, der ein Zertifikat in den Zertifikat Speicher für vertrauenswürdige Stamm Zertifizierungsstellen einfügt. Standardmäßig ist der Zertifikat Speicher für vertrauenswürdige Stamm Zertifizierungsstellen mit einer Gruppe von öffentlichen Zertifizierungsstellen konfiguriert, die die Anforderungen des Microsoft-Programms für Stamm Zertifikate erfüllt haben. |
| CA5381 | [CA5381: Stellen Sie sicher, dass keine Zertifikate zum Stammspeicher hinzugefügt werden.](../code-quality/ca5381.md) | Mit dieser Regel wird Code erkannt, der potenziell ein Zertifikat in den Zertifikat Speicher für vertrauenswürdige Stamm Zertifizierungsstellen einfügt. Standardmäßig ist der Zertifikat Speicher für vertrauenswürdige Stamm Zertifizierungsstellen mit einer Reihe von öffentlichen Zertifizierungsstellen (CAS) konfiguriert, die die Anforderungen des Microsoft-Programms für Stamm Zertifikate erfüllen. |
| CA5382 | [CA5382 Verwenden von sicheren Cookies in ASP.net Core](../code-quality/ca5382.md) | Anwendungen, die über HTTPS verfügbar sind, müssen sichere Cookies verwenden, die dem Browser zeigen, dass das Cookie nur mit Secure Sockets Layer (SSL) übertragen werden soll. |
| CA5383 | [CA5383 sicherstellen der Verwendung von sicheren Cookies in ASP.net Core](../code-quality/ca5383.md) | Anwendungen, die über HTTPS verfügbar sind, müssen sichere Cookies verwenden, die dem Browser zeigen, dass das Cookie nur mit Secure Sockets Layer (SSL) übertragen werden soll. |
| CA5384 | [CA5384 verwenden Sie den Digital Signature-Algorithmus (DSA) nicht.](../code-quality/ca5384.md) | DSA ist ein schwacher Algorithmus für die asymmetrische Verschlüsselung. |
| CA5385 | [CA5385 use Rivest – Shamir – Adleman (RSA)-Algorithmus mit ausreichender Schlüsselgröße](../code-quality/ca5385.md) | Ein RSA-Schlüssel, der kleiner als 2048 Bits ist, ist anfälliger für Brute-Force-Angriffe. |
| CA5386 | [CA5386: Vermeiden Sie die Hartcodierung des SecurityProtocolType-Werts.](../code-quality/ca5386.md) | Transport Layer Security (TLS) sichert die Kommunikation zwischen Computern, in der Regel mit HTTPS (Hypertext Transfer Protocol Secure). Die Protokoll Versionen TLS 1,0 und TLS 1,1 sind veraltet, TLS 1,2 und TLS 1,3 sind jedoch aktuell. In Zukunft können TLS 1,2 und TLS 1,3 als veraltet eingestuft werden. Um sicherzustellen, dass Ihre Anwendung sicher bleibt, vermeiden Sie das hart codieren einer Protokollversion und das Ziel mindestens .NET Framework v-4.7.1. |
| CA5387 | [CA5387 verwenden Sie keine schwache Schlüssel abderivations Funktion mit unzureichender Iterations Anzahl.](../code-quality/ca5387.md) | Mit dieser Regel wird überprüft, ob von ein Kryptografieschlüssel <xref:System.Security.Cryptography.Rfc2898DeriveBytes> mit einer Iterations Anzahl von weniger als 100.000 generiert wurde. Eine höhere iterations Anzahl kann bei der Vermeidung von Wörterbuchangriffen helfen, die versuchen, den generierten kryptografischen Schlüssel zu erraten. |
| CA5388 | [CA5388 bei Verwendung der Funktion für die schwache Schlüssel Ableitung eine ausreichende Anzahl von Iterationen sicherstellen](../code-quality/ca5388.md) | Mit dieser Regel wird überprüft, ob von ein Kryptografieschlüssel <xref:System.Security.Cryptography.Rfc2898DeriveBytes> mit einer Iterations Anzahl generiert wurde, die möglicherweise kleiner als 100.000 ist. Eine höhere iterations Anzahl kann bei der Vermeidung von Wörterbuchangriffen helfen, die versuchen, den generierten kryptografischen Schlüssel zu erraten. |
| CA5389 | [CA5389: Fügen Sie den Pfad des Archivelements nicht zum Pfad des Zieldateisystems hinzu.](../code-quality/ca5389.md) | Der Dateipfad kann relativ sein und kann dazu führen, dass der Dateisystem Zugriff außerhalb des erwarteten Ziel Pfads für das Dateisystem ist, was zu schädlichen Konfigurationsänderungen und Remote Codeausführung über die Methode "Lay-and-Wait" führt. |
| CA5390 | [CA5390 Verschlüsselungsschlüssel nicht hart codieren](../code-quality/ca5390.md) | Damit ein symmetrischer Algorithmus erfolgreich ist, muss der geheime Schlüssel nur dem Absender und dem Empfänger bekannt sein. Wenn ein Schlüssel hart codiert ist, kann er leicht erkannt werden. Selbst bei kompilierten Binärdateien ist es für böswillige Benutzer leicht, Sie zu extrahieren. Nachdem der private Schlüssel kompromittiert wurde, kann der Chiffre Text direkt entschlüsselt werden und ist nicht mehr geschützt. |
| CA5391 | [CA5391 Verwenden von antifälschungstoken in ASP.net Core MVC-Controllern](../code-quality/ca5391.md) | Das Verarbeiten einer- `POST` ,-,-oder-Anforderung, `PUT` `PATCH` `DELETE` ohne ein antifälschungstoken zu validieren, kann für Website übergreifende Anforderungs Fälschungs Angriffe anfällig sein. Mit einem Website übergreifenden Anforderungs Fälschungs Angriff können böswillige Anforderungen von einem authentifizierten Benutzer an Ihren ASP.net Core MVC-Controller gesendet werden. |
| CA5392 | [CA5392 Verwenden des defaultdllimportsearchpath-Attributs für P/Aufrufe](../code-quality/ca5392.md) | Standardmäßig verwenden P/aufrufen Funktionen, indem Sie <xref:System.Runtime.InteropServices.DllImportAttribute> eine Reihe von Verzeichnissen testen, einschließlich des aktuellen Arbeitsverzeichnisses für die zu ladende Bibliothek. Dies kann ein Sicherheitsproblem für bestimmte Anwendungen sein, was zu einer DLL-Hijacking-Aktion führt. |
| CA5393 | [CA5393 verwenden Sie keinen unsicheren dllimportsearchpath-Wert.](../code-quality/ca5393.md) | In den standardmäßigen dll-Such Verzeichnissen und Assemblyverzeichnissen könnte eine bösartige dll vorhanden sein. Abhängig davon, wo Ihre Anwendung ausgeführt wird, kann es sich auch um eine bösartige dll im Verzeichnis der Anwendung handeln. |
| CA5394 | [CA5394 verwenden Sie keine unsichere Zufälligkeit.](../code-quality/ca5394.md) | Die Verwendung eines kryptografisch schwachen Pseudozufallszahlen-Generators kann es einem Angreifer ermöglichen, vorherzusagen, welcher sicherheitsrelevante Wert generiert wird. |
| CA5395 | [CA5395 Miss httpVerb-Attribut für Aktionsmethoden](../code-quality/ca5395.md) | Alle Aktionsmethoden, die Daten erstellen, bearbeiten, löschen oder anderweitig ändern, müssen durch das antifälschungs Attribut von Website übergreifenden Anforderungs Fälschungs Angriffen geschützt werden. Das Ausführen eines Get-Vorgangs sollte ein sicherer Vorgang sein, der keine Nebeneffekte hat und die beibehaltenen Daten nicht ändert. |
| CA5396 | [CA5396 legen Sie HttpOnly für HttpCookie auf true fest.](../code-quality/ca5396.md) | Stellen Sie sicher, dass sicherheitsrelevante http-Cookies als "HttpOnly" gekennzeichnet sind. Dies bedeutet, dass Webbrowser das Zugreifen auf die Cookies durch Skripts nicht zulassen sollten. Injizierte schädliche Skripts sind eine gängige Methode zum stehlen von Cookies. |
| CA5397 | [CA5397: Verwenden Sie keine veralteten SslProtocols-Werte.](../code-quality/ca5397.md) | Transport Layer Security (TLS) sichert die Kommunikation zwischen Computern, in der Regel mit HTTPS (Hypertext Transfer Protocol Secure). Ältere Protokoll Versionen von TLS sind weniger sicher als TLS 1,2 und TLS 1,3 und haben wahrscheinlich neue Sicherheitsrisiken. Vermeiden Sie ältere Protokoll Versionen, um Risiken zu minimieren. |
| CA5398 | [CA5398: Vermeiden Sie hartcodierte SslProtocols-Werte.](../code-quality/ca5398.md) | Transport Layer Security (TLS) sichert die Kommunikation zwischen Computern, in der Regel mit HTTPS (Hypertext Transfer Protocol Secure). Die Protokoll Versionen TLS 1,0 und TLS 1,1 sind veraltet, TLS 1,2 und TLS 1,3 sind jedoch aktuell. In Zukunft können TLS 1,2 und TLS 1,3 als veraltet eingestuft werden. Vermeiden Sie das hart codieren einer Protokollversion, um sicherzustellen, dass Ihre Anwendung sicher bleibt. |
| CA5399 | [CA5399 Überprüfung der httpclient-Zertifikat Sperr Liste definitiv deaktivieren](../code-quality/ca5399.md) | Ein gesperrtes Zertifikat ist nicht mehr vertrauenswürdig. Sie kann von Angreifern verwendet werden, die bei der HTTPS-Kommunikation schädliche Daten übergeben oder vertrauliche Daten stehlen. |
| CA5400 | [CA5400 stellen Sie sicher, dass die Überprüfung der httpclient-Zertifikat Sperr Liste nicht](../code-quality/ca5400.md) | Ein gesperrtes Zertifikat ist nicht mehr vertrauenswürdig. Sie kann von Angreifern verwendet werden, die bei der HTTPS-Kommunikation schädliche Daten übergeben oder vertrauliche Daten stehlen. |
| CA5401 | [CA5401 verwenden Sie nicht "" für nicht standardmäßige IV.](../code-quality/ca5401.md) | Die symmetrische Verschlüsselung sollte immer einen nicht wiederholbaren Initialisierungs Vektor verwenden, um Wörterbuchangriffe zu verhindern. |
| CA5402 | [CA5402 Verwenden von "kreateverschlüsseltor" mit dem Standard-IV](../code-quality/ca5402.md) | Die symmetrische Verschlüsselung sollte immer einen nicht wiederholbaren Initialisierungs Vektor verwenden, um Wörterbuchangriffe zu verhindern. |
| CA5403 | [CA5403: Keine Hartcodierung von Zertifikaten](../code-quality/ca5403.md) | Der `data` - `rawData` Parameter oder der-Parameter eines- <xref:System.Security.Cryptography.X509Certificates.X509Certificate> oder- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> Konstruktors ist hart codiert. |
| IL3000 | [IL3000 keinen Zugriff auf den assemblydateipfad beim Veröffentlichen als einzelne Datei vermeiden](../code-quality/il3000.md) | Vermeiden Sie das Zugreifen auf den assemblydateipfad beim Veröffentlichen als einzelne Datei. |
| IL3001 | [IL3001 vermeiden Sie den Zugriff auf den assemblydateipfad beim Veröffentlichen als Einzel Datei.](../code-quality/il3001.md) | Vermeiden des Zugriffs auf den assemblydateipfad beim Veröffentlichen als Einzel Datei |
