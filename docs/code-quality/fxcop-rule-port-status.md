---
title: Port Status der FxCop-Regel
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508365"
---
# <a name="fxcop-rule-port-status"></a>Port Status der FxCop-Regel

Wenn Sie zuvor eine statische Code Analyse in Visual Studio verwendet haben, Fragen Sie sich vielleicht, welche dieser Regeln in der aktuellen Implementierung als [FxCop-Analysen](install-fxcop-analyzers.md)verfügbar sind. Auf dieser Seite werden die Regeln aufgelistet, die portiert wurden. Weitere Informationen finden Sie unter [nicht portierte Regeln](fxcop-unported-rules.md) für diejenigen, die nicht portiert wurden, und ob Pläne zum Portieren vorhanden sind.

## <a name="ported-rules"></a>Portierte Regeln

Die [Seite für die automatisch generierte Dokumentation](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) im Repository "Roslyn-Analyzers" enthält die aktuellste Liste der Regeln, die in FxCop-Analyzers portiert wurden. Diese Seite verfügt auch über zusätzliche Informationen, z. b. ob die Regel standardmäßig aktiviert ist und ob Sie über eine zugeordnete *Code Korrektur*verfügt. ([Code Fehlerbehebungen](../ide/quick-actions.md) sind One-Click-Korrekturen, die im Glühbirnen-Symbolmenü in Visual Studio verfügbar sind.)

Die Liste der FxCop-Regeln, die zu den [FxCop-Analyzern](install-fxcop-analyzers.md) portiert wurden, entspricht dem Datum auf dieser Seite:

Regel-ID | Titel
--------|---------
[CA1000](ca1000.md) | Statische Member nicht in generischen Typen deklarieren.
[CA1001](ca1001.md) | Typen, die löschbare Felder besitzen, müssen gelöscht werden können.
[CA1002](ca1002.md) | Generische Listen nicht verfügbar machen.
[CA1003](ca1003.md) | Generische Ereignishandlerinstanzen verwenden.
[CA1005](ca1005.md) | Übermäßige Anzahl von Parametern in generischen Typen vermeiden.
[CA1008](ca1008.md) | Enumerationen müssen einen Wert von 0 (null) aufweisen.
[CA1010](ca1010.md) | Sammlungen müssen eine generische Schnittstelle implementieren.
[CA1012](ca1012.md) | Abstrakte Typen dürfen keine Konstruktoren aufweisen.
[CA1014](ca1014.md) | Assemblys mit clscompliance markieren
[CA1016](ca1016.md) | Assemblys mit Assembly-Version markieren
[CA1017](ca1017.md) | Assemblys mit ComVisible markieren
[CA1018](ca1018.md) | Attribute mit AttributeUsageAttribute markieren.
[CA1019](ca1019.md) | Accessoren für Attributargumente definieren.
[CA1021](ca1021.md) | out-Parameter vermeiden.
[CA1024](ca1024.md) | Nach Möglichkeit Eigenschaften verwenden.
[CA1027](ca1027.md) | Enumerationen mit FlagsAttribute markieren.
[CA1028](ca1028.md) | Der Aufzählungs Speicher muss Int32 lauten.
[CA1030](ca1030.md) | Nach Möglichkeit Ereignisse verwenden.
[CA1031](ca1031.md) | Allgemeine Ausnahmetypen nicht auffangen.
[CA1032](ca1032.md) | Standardausnahmekonstruktoren implementieren.
[CA1033](ca1033.md) | Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.
[CA1034](ca1034.md) | Geschachtelte Typen sollten nicht sichtbar sein.
[CA1036](ca1036.md) | Methoden bei vergleichbaren Typen überschreiben.
[CA1040](ca1040.md) | Leere Schnittstellen vermeiden.
[CA1041](ca1041.md) | ObsoleteAttribute-Meldung bereitstellen.
[CA1043](ca1043.md) | Ganzzahliges Argument oder Zeichen folgen Argument für Indexer verwenden
[CA1044](ca1044.md) | Eigenschaften sollten nicht lesegeschützt sein.
[CA1045](ca1045.md) | Typen nicht als Verweis übergeben.
[CA1046](ca1046.md) | Gleichheitsoperator für Referenztypen nicht überladen.
[CA1047](ca1047.md) | Geschützte Member in versiegelten Typen nicht deklarieren.
[CA1050](ca1050.md) | Typen in Namespaces deklarieren.
[CA1051](ca1051.md) | Sichtbare Instanzfelder nicht deklarieren.
[CA1052](ca1052.md) | Statische Halter Typen sollten statisch oder notgeerbt sein.
[CA1053](ca1053.md) | Statische Halter Typen sollten keine Konstruktoren aufweisen (CA1053 ist Teil von [CA1052](ca1052.md) für FxCop-Analyzers).
[CA1054](ca1054.md) | URI-Parameter dürfen keine Zeichen folgen sein.
[CA1055](ca1055.md) | URI-Rückgabewerte dürfen keine Zeichen folgen sein.
[CA1056](ca1056.md) | Uri-Eigenschaften dürfen keine Zeichen folgen sein.
[CA1058](ca1058.md) | Typen sollten bestimmte Basistypen nicht erweitern.
[CA1060](ca1060.md) | PInvokes in systemeigene Methoden Klasse verschieben
[CA1061](ca1061.md) | Basisklassenmethoden nicht ausblenden.
[CA1062](ca1062.md) | Argumente von öffentlichen Methoden validieren.
[CA1063](ca1063.md) | Ordnungsgemäße Implementierung von iverwerf
[CA1064](ca1064.md) | Ausnahmen sollten öffentlich sein.
[CA1065](ca1065.md) | Keine Ausnahmen an unerwarteten Speicherorten auslösen.
[CA1066](ca1066.md) | Der Typ {0} muss "IEquatable" implementieren, \<T> da er "ist mit"
[CA1067](ca1067.md) | Überschreiben Sie Object. Gleichheits (Objekt), wenn Sie IEquatable implementieren.\<T>
[CA1303](ca1303.md) | Literale nicht als lokalisierte Parameter übergeben.
[CA1304](ca1304.md) | CultureInfo angeben.
[CA1305](ca1305.md) | IFormatProvider angeben.
[CA1307](ca1307.md) | StringComparison zur Übersichtlichkeit angeben
[CA1308](ca1308.md) | Zeichenfolgen in Großbuchstaben normalisieren.
[CA1309](ca1309.md) | Ordinalzeichenfolgen-Vergleich verwenden
[CA1401](ca1401.md) | P/Invokes dürfen nicht sichtbar sein.
[CA1501](ca1501.md) | Übermäßige Vererbung vermeiden.
[CA1502](ca1502.md) | Übermäßige Komplexität vermeiden.
[CA1505](ca1505.md) | Nicht wartbaren Code vermeiden.
[CA1506](ca1506.md) | Übermäßige Klassenkopplungen vermeiden.
[CA1700](ca1700.md) | Enumerationswerte nicht mit "Reserviert" benennen.
[CA1707](ca1707.md) | Bezeichner sollten keine Unterstriche enthalten.
[CA1708](ca1708.md) | Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.
[CA1710](ca1710.md) | Bezeichner sollten ein richtiges Suffix aufweisen.
[CA1711](ca1711.md) | Bezeichner sollten kein falsches Suffix aufweisen.
[CA1712](ca1712.md) | Keine Typnamen als Präfixe für Enumerationswerte verwenden.
[CA1713](ca1713.md) | Ereignisse sollten kein Before- oder After-Präfix aufweisen.
[CA1714](ca1714.md) | Flags-Enumerationen sollten Pluralnamen aufweisen.
[CA1715](ca1715.md) | Bezeichner sollten ein korrektes Präfix aufweisen.
[CA1716](ca1716.md) | Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.
[CA1717](ca1717.md) | Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.
[CA1720](ca1720.md) | Bezeichner enthält Typnamen
[CA1721](ca1721.md) | Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[CA1724](ca1724.md) | Typnamen sollten nicht mit Namespaces identisch sein.
[CA1725](ca1725.md) | Parameternamen sollten mit der Basisdeklaration übereinstimmen.
[CA1801](ca1801.md) | Nicht verwendete Parameter überprüfen.
[CA1802](ca1802.md) | Verwenden Sie nach Bedarf Literale.
[CA1805](ca1805.md) | Nicht unnötig initialisieren
[CA1806](ca1806.md) | Methodenergebnisse nicht ignorieren.
[CA1810](ca1810.md) | Statische Felder von Referenztypen inline initialisieren.
[CA1812](ca1812.md) | Nicht instanziierte interne Klassen vermeiden.
[CA1813](ca1813.md) | Nicht versiegelte Attribute vermeiden.
[CA1814](ca1814.md) | Jagged Arrays mehrdimensionalen Arrays vorziehen.
[CA1815](ca1815.md) | Equals und Gleichheitsoperator für Werttypen überschreiben.
[CA1816](ca1816.md) | Verwerfen von Methoden sollten SuppressFinalize aufgerufen werden.
[CA1819](ca1819.md) | Eigenschaften sollten keine Arrays zurückgeben.
[CA1820](ca1820.md) | Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.
[CA1821](ca1821.md) | Leere Finalizer entfernen
[CA1822](ca1822.md) | Member als statisch markieren.
[CA1823](ca1823.md) | Nicht verwendete private Felder vermeiden.
[CA1824](ca1824.md) | Assemblys mit NeutralResourcesLanguageAttribute markieren.
[CA1825](ca1825.md) | Vermeiden Sie Array Belegungen der Länge 0 (null).
[CA2000](ca2000.md) | Objekte verwerfen, bevor Bereich verloren geht.
[CA2002](ca2002.md) | Auf Objekten mit schwacher Identität nicht sperren.
[CA2100](ca2100.md) | SQL-Abfragen auf Sicherheitsrisiken überprüfen.
[CA2101](ca2101.md) | Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.
[CA2109](ca2109.md) | Sichtbare Ereignishandler überprüfen.
[CA2119](ca2119.md) | Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.
[CA2153](ca2153.md) | Beschädigte Zustands Ausnahmen nicht erfassen
[CA2200](ca2200.md) | Erneut auslösen, um Stapel Details beizubehalten.
[CA2201](ca2201.md) | Keine reservierten Ausnahmetypen auslösen.
[CA2207](ca2207.md) | Statische Felder für Werttyp inline initialisieren.
[CA2208](ca2208.md) | Argumentausnahmen korrekt instanziieren.
[CA2211](ca2211.md) | Nicht konstante Felder sollten nicht sichtbar sein.
[CA2213](ca2213.md) | Verwerfbare Felder verwerfen.
[CA2214](ca2214.md) | Überschreibbare Methoden in Konstruktoren nicht aufrufen.
[CA2215](ca2215.md) | Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.
[CA2216](ca2216.md) | Verwerfbare Typen sollten einen Finalizer deklarieren.
[CA2217](ca2217.md) | Enumerationen nicht mit FlagsAttribute markieren.
[CA2219](ca2219.md) | Keine Ausnahmen in den Schluss Klauseln
[CA2225](ca2225.md) | Operatorüberladungen weisen benannte Alternativen auf.
[CA2226](ca2226.md) | Operatoren sollten symmetrische Überladungen aufweisen.
[CA2227](ca2227.md) | Sammlungseigenschaften sollten schreibgeschützt sein.
[CA2229](ca2229.md) | Serialisierungskonstruktoren implementieren.
[CA2231](ca2231.md) | Gleichheits Operator beim Überschreiben des Werttyps
[CA2234](ca2234.md) | Übergeben von System-Uri-Objekten anstelle von Zeichen folgen
[CA2235](ca2235.md) | Alle nicht serialisierbaren Felder markieren.
[CA2237](ca2237.md) | ISerializable-Typen als serialisierbar markieren
[CA2241](ca2241.md) | Geben Sie die korrekte Anzahl für Formatierungsmethoden an.
[CA2242](ca2242.md) | Ordnungsgemäß auf NaN testen.
[CA2243](ca2243.md) | Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.
[CA2300](ca2300.md) | Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden
[CA2301](ca2301.md) | BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen
[CA2302](ca2302.md) | Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen
[CA2305](ca2305.md) | Unsicheren Deserialisierer nicht verwenden: LosFormatter
[CA2310](ca2310.md) | Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer
[CA2311](ca2311.md) | Nicht deserialisieren, ohne zuerst NetDataContractSerializer.Binder festzulegen
[CA2312](ca2312.md) | Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist
[CA2315](ca2315.md) | Unsicheren Deserialisierer nicht verwenden: ObjectStateFormatter
[CA2321](ca2321.md) | Nicht mit JavaScriptSerializer und SimpleTypeResolver deserialisieren
[CA2322](ca2322.md) | Vor dem Deserialisieren sicherstellen, dass JavaScriptSerializer nicht mit SimpleTypeResolver initialisiert ist
[CA3001](ca3001.md) | Review code for SQL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von SQL-Befehlen)
[CA3002](ca3002.md) | Review code for XSS vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch XSS)
[CA3003](ca3003.md) | Review code for file path injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen über einen Dateipfad)
[CA3004](ca3004.md) | Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)
[CA3005](ca3005.md) | Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)
[CA3006](ca3006.md) | Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)
[CA3007](ca3007.md) | Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)
[CA3008](ca3008.md) | Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)
[CA3009](ca3009.md) | Review code for XML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XML-Befehlen)
[CA3010](ca3010.md) | Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)
[CA3011](ca3011.md) | Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)
[CA3012](ca3012.md) | Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)
[CA3061](ca3061.md) | Schema nicht nach URL hinzufügen
[CA3075](ca3075.md) | Unsichere DTD-Verarbeitung in XML
[CA3076](ca3076.md) | Unsichere XSLT-Skript Verarbeitung.
[CA3077](ca3077.md) | Unsichere Verarbeitung in API-Design, XmlDocument und XmlTextReader
[CA3147](ca3147.md) | Markieren von Verb Handlern mit Token zum Überprüfen der Antifälschung
[CA5350](ca5350.md) | Keine schwachen Kryptografiealgorithmen verwenden.
[CA5351](ca5351.md) | Verwenden Sie keine unterbrochenen Kryptografiealgorithmen.
[CA5358](ca5358.md) | Verwenden Sie keine unsicheren Verschlüsselungsmodi.
CA5359 | Zertifikat Überprüfung nicht deaktivieren
CA5360 | Keine gefährlichen Methoden bei der Deserialisierung aufzurufen
[CA5361](ca5361.md) | Die SChannel-Verwendung der starken Kryptografie nicht deaktivieren
CA5362 | In der serialisierbaren Klasse nicht auf sich selbst verweisen
[CA5363](ca5363.md) | Anforderungs Validierung nicht deaktivieren
[CA5364](ca5364.md) | Veraltete Sicherheitsprotokolle nicht verwenden
CA5365 | HTTP-Header Überprüfung nicht deaktivieren
CA5366 | Verwenden von XmlReader für DataSet-Lese-XML
CA5367 | Typen mit Zeiger Feldern nicht serialisieren
CA5368 | Festlegen von "VIEWSTATUS User Key" für von der Seite abgeleitete Klassen
[CA5369](ca5369.md) | XmlReader für die Deserialisierung verwenden
[CA5370](ca5370.md) | Verwenden von XmlReader zum Überprüfen des Readers
[CA5371](ca5371.md) | Verwenden von XmlReader für Schema Lesevorgänge
[CA5372](ca5372.md) | XmlReader für XPathDocument verwenden
[CA5373](ca5373.md) | Verwenden Sie keine veraltete Schlüsselableitungsfunktion.
CA5374 | XslTransform nicht verwenden
CA5375 | Konto Shared Access Signature nicht verwenden
CA5376 | Verwenden von sharedaccessproycol httpsonly
CA5377 | Zugriffs Richtlinie auf Container Ebene verwenden
[CA5378](ca5378.md) | Deaktivieren Sie ServicePointManagerSecurityProtocols nicht.
CA5379 | Algorithmus für schwache Schlüssel abderivations Funktion nicht verwenden
CA9999 | Konflikt bei der Analyzer-Version

## <a name="see-also"></a>Weitere Informationen

- [Microsoft. Code Analysis. fxcopanalyzers-Regeln](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
