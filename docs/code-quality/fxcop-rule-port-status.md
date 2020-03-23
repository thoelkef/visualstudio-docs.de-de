---
title: FxCop-Regelportstatus
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
ms.openlocfilehash: fccd167bfafd4c27895b01927aaabc1e77eab91c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301608"
---
# <a name="fxcop-rule-port-status"></a>Fxcop-Regelportstatus

Wenn Sie zuvor statische Codeanalyse in Visual Studio verwendet haben, fragen Sie sich möglicherweise, welche dieser Regeln in der aktuellen Implementierung als [FxCop-Analysatoren](install-fxcop-analyzers.md)verfügbar sind. Auf dieser Seite werden die Regeln aufgeführt, die portiert werden, sowie die Regeln, die nicht portiert wurden, und ob es Pläne für deren Portierung gibt.

## <a name="ported-rules"></a>Portierte Regeln

Die [automatisch generierte Dokumentationsseite](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) im Repo für Roslyn-Analyzer enthält die aktuellste Liste von Regeln, die auf FxCop-Analysatoren portiert wurden. Diese Seite enthält auch zusätzliche Informationen, z. B. ob die Regel standardmäßig aktiviert ist und ob sie über einen zugeordneten *Codefix verfügt.* ([Codefixes](../ide/quick-actions.md) sind Ein-Klick-Fixes, die im Glühbirnensymbolmenü in Visual Studio verfügbar sind.)

Ab dem Datum auf dieser Seite enthält die Liste der FxCop-Regeln, die auf [FxCop-Analysatoren](install-fxcop-analyzers.md) portiert wurden, Folgendes:

Regel-ID | Titel
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Statische Member nicht in generischen Typen deklarieren.
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Typen, die löschbare Felder besitzen, müssen gelöscht werden können.
[CA1003](ca1003-use-generic-event-handler-instances.md) | Generische Ereignishandlerinstanzen verwenden.
[CA1008](ca1008-enums-should-have-zero-value.md) | Enumerationen müssen einen Wert von 0 (null) aufweisen.
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Sammlungen müssen eine generische Schnittstelle implementieren.
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Abstrakte Typen dürfen keine Konstruktoren aufweisen.
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Markieren von Assemblys mit CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Markieren von Baugruppen mit Baugruppenversion
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Markieren von Assemblys mit ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Attribute mit AttributeUsageAttribute markieren.
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Accessoren für Attributargumente definieren.
[CA1021](ca1021.md) | out-Parameter vermeiden.
[CA1024](ca1024-use-properties-where-appropriate.md) | Nach Möglichkeit Eigenschaften verwenden.
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Enumerationen mit FlagsAttribute markieren.
[CA1028](ca1028-enum-storage-should-be-int32.md) | Enum Storage sollte Int32 sein
[CA1030](ca1030-use-events-where-appropriate.md) | Nach Möglichkeit Ereignisse verwenden.
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Allgemeine Ausnahmetypen nicht auffangen.
[CA1032](ca1032-implement-standard-exception-constructors.md) | Standardausnahmekonstruktoren implementieren.
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Geschachtelte Typen sollten nicht sichtbar sein.
[CA1036](ca1036-override-methods-on-comparable-types.md) | Methoden bei vergleichbaren Typen überschreiben.
[CA1040](ca1040-avoid-empty-interfaces.md) | Leere Schnittstellen vermeiden.
[CA1041](ca1041-provide-obsoleteattribute-message.md) | ObsoleteAttribute-Meldung bereitstellen.
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Integral- oder Zeichenfolgenargument für Indexer verwenden
[CA1044](ca1044-properties-should-not-be-write-only.md) | Eigenschaften sollten nicht lesegeschützt sein.
[CA1050](ca1050-declare-types-in-namespaces.md) | Typen in Namespaces deklarieren.
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Sichtbare Instanzfelder nicht deklarieren.
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Statische Haltertypen sollten statisch oder nicht vererbbar sein
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Statische Haltertypen sollten keine Konstruktoren haben (CA1053 ist Teil von [CA1052](ca1052-static-holder-types-should-be-sealed.md) für FxCop-Analysatoren)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | URI-Parameter sollten keine Zeichenfolgen sein
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Uri-Rückgabewerte sollten keine Zeichenfolgen sein
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Uri-Eigenschaften sollten keine Zeichenfolgen sein
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Typen sollten bestimmte Basistypen nicht erweitern.
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Verschieben von Pinvokes in die Klasse der systemeigenen Methoden
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Basisklassenmethoden nicht ausblenden.
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Argumente von öffentlichen Methoden validieren.
[CA1063](ca1063-implement-idisposable-correctly.md) | IDisposable korrekt implementieren
[CA1064](ca1064-exceptions-should-be-public.md) | Ausnahmen sollten öffentlich sein.
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Keine Ausnahmen an unerwarteten Speicherorten auslösen.
CA1066 | Typ {0} sollte IEquatable T> implementieren,\<da er Equals überschreibt
CA1067 | Override Object.Equals(object) bei der\<Implementierung von IEquatable T>
[CA1068](ca1068.md) | CancellationToken-Parameter müssen zuletzt aufgeführt werden.
CA1200 | Verwenden Sie keine cref-Tags mit einem Präfix.
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Literale nicht als lokalisierte Parameter übergeben.
[CA1304](ca1304-specify-cultureinfo.md) | CultureInfo angeben.
[CA1305](ca1305-specify-iformatprovider.md) | IFormatProvider angeben.
[CA1307](ca1307-specify-stringcomparison.md) | StringComparison angeben.
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Zeichenfolgen in Großbuchstaben normalisieren.
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Ordinalzeichenfolgenvergleich verwenden
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | P/Invokes dürfen nicht sichtbar sein.
[CA1501](ca1501-avoid-excessive-inheritance.md) | Übermäßige Vererbung vermeiden.
[CA1502](ca1502-avoid-excessive-complexity.md) | Übermäßige Komplexität vermeiden.
[CA1505](ca1505-avoid-unmaintainable-code.md) | Nicht wartbaren Code vermeiden.
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Übermäßige Klassenkopplungen vermeiden.
[CA1507](ca1507.md) | Verwenden des Namens von zum Ausdrücken von Symbolnamen
CA1508 | Vermeiden Sie toten bedingten Code
CA1509 | Ungültiger Eintrag in der Regelspezifikationsdatei für Codemetriken
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Bezeichner sollten keine Unterstriche enthalten.
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Bezeichner sollten ein richtiges Suffix aufweisen.
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Bezeichner sollten kein falsches Suffix aufweisen.
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Keine Typnamen als Präfixe für Enumerationswerte verwenden.
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Flags-Enumerationen sollten Pluralnamen aufweisen.
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Bezeichner sollten ein korrektes Präfix aufweisen.
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Bezeichner enthält Typname
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Typnamen sollten nicht mit Namespaces übereinstimmen
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Parameternamen sollten mit der Basisdeklaration übereinstimmen.
[CA1801](ca1801.md) | Nicht verwendete Parameter überprüfen.
[CA1802](ca1802.md) | Verwenden Sie die Literale, wo dies angebracht ist
[CA1806](ca1806.md) | Methodenergebnisse nicht ignorieren.
[CA1810](ca1810.md) | Statische Felder von Referenztypen inline initialisieren.
[CA1812](ca1812.md) | Nicht instanziierte interne Klassen vermeiden.
[CA1813](ca1813.md) | Nicht versiegelte Attribute vermeiden.
[CA1814](ca1814.md) | Jagged Arrays mehrdimensionalen Arrays vorziehen.
[CA1815](ca1815.md) | Equals und Gleichheitsoperator für Werttypen überschreiben.
[CA1816](ca1816.md) | Dispose-Methoden sollten SuppressFinalize aufrufen
[CA1819](ca1819.md) | Eigenschaften sollten keine Arrays zurückgeben.
[CA1820](ca1820.md) | Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.
[CA1821](ca1821.md) | Entfernen leerer Finalizer
[CA1822](ca1822.md) | Member als statisch markieren.
[CA1823](ca1823.md) | Nicht verwendete private Felder vermeiden.
[CA1824](ca1824.md) | Assemblys mit NeutralResourcesLanguageAttribute markieren.
CA1825 | Vermeiden Sie Arrayzuordnungen mit einer Länge von Null.
CA1826 | Verwenden Sie keine Enumerable-Methoden für indexierbare Auflistungen. Verwenden Sie stattdessen die Auflistung direkt
[CA2000](ca2000.md) | Objekte verwerfen, bevor Bereich verloren geht.
[CA2002](ca2002.md) | Auf Objekten mit schwacher Identität nicht sperren.
[CA2007](ca2007.md) | Erwägen Sie, ConfigureAwait für die erwartete Aufgabe aufzurufen.
CA2008 | Erstellen Sie keine Aufgaben, ohne einen TaskScheduler zu übergeben.
CA2009 | ToImmutableCollection nicht für einen Unveränderlichen Auflistungswert aufrufen
CA2010 | Verwenden Sie immer den Wert, der von Methoden zurückgegeben wird, die mit PreserveSigAttribute markiert sind.
[CA2100](ca2100.md) | SQL-Abfragen auf Sicherheitsrisiken überprüfen.
[CA2101](ca2101.md) | Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.
[CA2119](ca2119.md) | Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.
[CA2153](ca2153.md) | Nicht fangen beschädigten Zustand Ausnahmen
[CA2200](ca2200.md) | Zurückwerfen, um Stapeldetails beizubehalten.
[CA2201](ca2201.md) | Keine reservierten Ausnahmetypen auslösen.
[CA2207](ca2207.md) | Statische Felder für Werttyp inline initialisieren.
[CA2208](ca2208.md) | Argumentausnahmen korrekt instanziieren.
[CA2211](ca2211.md) | Nicht konstante Felder sollten nicht sichtbar sein.
[CA2213](ca2213.md) | Verwerfbare Felder verwerfen.
[CA2214](ca2214.md) | Überschreibbare Methoden in Konstruktoren nicht aufrufen.
[CA2216](ca2216.md) | Verwerfbare Typen sollten einen Finalizer deklarieren.
[CA2217](ca2217.md) | Enumerationen nicht mit FlagsAttribute markieren.
[CA2218](ca2218.md) | GetHashCode beim Überschreiben von Equals überschreiben.
[CA2219](ca2219.md) | Keine Ausnahmen in finally-Klauseln
[CA2224](ca2224.md) | Überschreiben gleich bei Überladen des Operators gleich
[CA2225](ca2225.md) | Operatorüberladungen weisen benannte Alternativen auf.
[CA2226](ca2226.md) | Operatoren sollten symmetrische Überladungen aufweisen.
[CA2227](ca2227.md) | Sammlungseigenschaften sollten schreibgeschützt sein.
[CA2229](ca2229.md) | Serialisierungskonstruktoren implementieren.
[CA2231](ca2231.md) | Überlastoperator gleich auf überschreibendem Werttyp Gleich
[CA2234](ca2234.md) | Passsystem uri-Objekte anstelle von Strings
[CA2235](ca2235.md) | Alle nicht serialisierbaren Felder markieren.
[CA2237](ca2237.md) | ISerializable-Typen als serialisierbar markieren
[CA2241](ca2241.md) | Geben Sie die korrekte Anzahl für Formatierungsmethoden an.
[CA2242](ca2242.md) | Ordnungsgemäß auf NaN testen.
[CA2243](ca2243.md) | Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.
CA2244 | Indizierende Elementinitialisierungen nicht duplizieren
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
CA3061 | Schema nicht nach URL hinzufügen
[CA3075](ca3075.md) | Unsichere DTD-Verarbeitung in XML
[CA3076](ca3076.md) | Unsichere XSLT-Skriptverarbeitung.
[CA3077](ca3077.md) | Unsichere Verarbeitung in API Design, XmlDocument und XmlTextReader
[CA3147](ca3147.md) | Markieren Verb Handler mit Validieren Antiforgery Token
[CA5350](ca5350.md) | Keine schwachen Kryptografiealgorithmen verwenden.
[CA5351](ca5351.md) | Verwenden Sie keine gebrochenen kryptografischen Algorithmen
CA5358 | Verwenden Sie keine unsicheren Verschlüsselungsmodi.
CA5359 | Zertifikatvalidierung nicht deaktivieren
CA5360 | Gefährliche Methoden bei Deserialisierung nicht aufrufen
CA5361 | Deaktivieren Sie nicht SChannel-Verwendung von Strong Crypto
CA5362 | Nicht selbst in Serializable-Klasse verweisen
CA5363 | Anforderungsüberprüfung nicht deaktivieren
CA5364 | Verwenden Sie keine veralteten Sicherheitsprotokolle
CA5365 | HTTP-Headerüberprüfung nicht deaktivieren
CA5366 | XmlReader für Dataset Read Xml verwenden
CA5367 | Nicht serialisieren von Typen mit Zeigerfeldern
CA5368 | Festlegen von ViewStateUserKey für Klassen, die von der Seite abgeleitet wurden
CA5369 | XmlReader für Deserialisierung verwenden
CA5370 | Verwenden von XmlReader zum Validieren des Lesegeräts
CA5371 | XmlReader für Schemalesen verwenden
CA5372 | XmlReader für XPathDocument verwenden
CA5373 | Verwenden Sie keine veraltete Schlüsselableitungsfunktion.
CA5374 | XslTransform nicht verwenden
CA5375 | Verwenden Sie keine Konto-Shared Access-Signatur
CA5376 | Verwenden von SharedAccessProtocol httpsOnly
CA5377 | Verwenden der Container-Level-Zugriffsrichtlinie
CA5378 | Deaktivieren Sie ServicePointManagerSecurityProtocols nicht.
CA5379 | Verwenden Sie keinen Schwachschlüssel-Ableitungsalgorithmus
CA9999 | Inübereinstimmung der Analyzer-Version

## <a name="unported-rules"></a>Nicht portierte Regeln

Der Satz von Regeln, der nicht auf [FxCop-Analysatoren](install-fxcop-analyzers.md) portiert wurde, besteht aus Regeln, die noch nicht [portiert werden können,](#rules-that-may-be-ported)und solchen, die veraltet sind und [nicht portiert werden.](#deprecated-rules)

### <a name="rules-that-may-be-ported"></a>Regeln, die portiert werden können

Die folgenden FxCop-Legacyanalyseregeln wurden noch nicht als Analysatoren implementiert, können es aber immer noch sein. Dies kann aus einem blockierenden technischen Grund sein oder einfach, dass die Regel eine niedrigere Priorität hat. Weitere Informationen zum Portierungsstatus jeder Regel erhalten Sie, wenn Sie auf den Link in der Spalte **Tracking-Problem** klicken.

Regel-ID | Tracking-Problem
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Veraltete Regeln

Die folgenden FxCop-Legacyanalyseregeln sind veraltet und werden nicht als Analysatoren implementiert. Weitere Informationen finden Sie auf der [Seite "Roslyn-Analyzer GitHub issues"](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port)nach Regel-ID (z. B. **CA1009**).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([Begründung](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Weitere Informationen

- [Microsoft.CodeAnalysis.FxCopAnalyzers-Regeln](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
