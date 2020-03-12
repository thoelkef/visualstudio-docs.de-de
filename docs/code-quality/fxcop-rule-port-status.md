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
ms.openlocfilehash: fccd167bfafd4c27895b01927aaabc1e77eab91c
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2020
ms.locfileid: "78945732"
---
# <a name="fxcop-rule-port-status"></a>Port Status der FxCop-Regel

Wenn Sie zuvor eine statische Code Analyse in Visual Studio verwendet haben, Fragen Sie sich vielleicht, welche dieser Regeln in der aktuellen Implementierung als [FxCop-Analysen](install-fxcop-analyzers.md)verfügbar sind. Auf dieser Seite sind die Regeln aufgeführt, die portiert werden, sowie diejenigen, die nicht portiert wurden, und es wird davon abgeraten, Sie zu portieren.

## <a name="ported-rules"></a>Portierte Regeln

Die [Seite für die automatisch generierte Dokumentation](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) im Repository "Roslyn-Analyzers" enthält die aktuellste Liste der Regeln, die in FxCop-Analyzers portiert wurden. Diese Seite verfügt auch über zusätzliche Informationen, z. b. ob die Regel standardmäßig aktiviert ist und ob Sie über eine zugeordnete *Code Korrektur*verfügt. ([Code Fehlerbehebungen](../ide/quick-actions.md) sind One-Click-Korrekturen, die im Glühbirnen-Symbolmenü in Visual Studio verfügbar sind.)

Die Liste der FxCop-Regeln, die zu den [FxCop-Analyzern](install-fxcop-analyzers.md) portiert wurden, entspricht dem Datum auf dieser Seite:

Regel-ID | Titel
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Statische Member nicht in generischen Typen deklarieren.
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Typen, die löschbare Felder besitzen, müssen gelöscht werden können.
[CA1003](ca1003-use-generic-event-handler-instances.md) | Generische Ereignishandlerinstanzen verwenden.
[CA1008](ca1008-enums-should-have-zero-value.md) | Enumerationen müssen einen Wert von 0 (null) aufweisen.
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Sammlungen müssen eine generische Schnittstelle implementieren.
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Abstrakte Typen dürfen keine Konstruktoren aufweisen.
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Assemblys mit clscompliance markieren
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Assemblys mit Assembly-Version markieren
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Assemblys mit ComVisible markieren
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Attribute mit AttributeUsageAttribute markieren.
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Accessoren für Attributargumente definieren.
[CA1021](ca1021.md) | out-Parameter vermeiden.
[CA1024](ca1024-use-properties-where-appropriate.md) | Nach Möglichkeit Eigenschaften verwenden.
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Enumerationen mit FlagsAttribute markieren.
[CA1028](ca1028-enum-storage-should-be-int32.md) | Der Aufzählungs Speicher muss Int32 lauten.
[CA1030](ca1030-use-events-where-appropriate.md) | Nach Möglichkeit Ereignisse verwenden.
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Allgemeine Ausnahmetypen nicht auffangen.
[CA1032](ca1032-implement-standard-exception-constructors.md) | Standardausnahmekonstruktoren implementieren.
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Geschachtelte Typen sollten nicht sichtbar sein.
[CA1036](ca1036-override-methods-on-comparable-types.md) | Methoden bei vergleichbaren Typen überschreiben.
[CA1040](ca1040-avoid-empty-interfaces.md) | Leere Schnittstellen vermeiden.
[CA1041](ca1041-provide-obsoleteattribute-message.md) | ObsoleteAttribute-Meldung bereitstellen.
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Ganzzahliges Argument oder Zeichen folgen Argument für Indexer verwenden
[CA1044](ca1044-properties-should-not-be-write-only.md) | Eigenschaften sollten nicht lesegeschützt sein.
[CA1050](ca1050-declare-types-in-namespaces.md) | Typen in Namespaces deklarieren.
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Sichtbare Instanzfelder nicht deklarieren.
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Statische Halter Typen sollten statisch oder notgeerbt sein.
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Statische Halter Typen sollten keine Konstruktoren aufweisen (CA1053 ist Teil von [CA1052](ca1052-static-holder-types-should-be-sealed.md) für FxCop-Analyzers).
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | URI-Parameter dürfen keine Zeichen folgen sein.
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | URI-Rückgabewerte dürfen keine Zeichen folgen sein.
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Uri-Eigenschaften dürfen keine Zeichen folgen sein.
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Typen sollten bestimmte Basistypen nicht erweitern.
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | PInvokes in systemeigene Methoden Klasse verschieben
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Basisklassenmethoden nicht ausblenden.
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Argumente von öffentlichen Methoden validieren.
[CA1063](ca1063-implement-idisposable-correctly.md) | Ordnungsgemäße Implementierung von iverwerf
[CA1064](ca1064-exceptions-should-be-public.md) | Ausnahmen sollten öffentlich sein.
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Keine Ausnahmen an unerwarteten Speicherorten auslösen.
CA1066 | Der Typ {0} sollte IEquatable\<t > implementieren, da er "was" überschreibt.
CA1067 | Überschreiben Sie Object. Gleichheits (Objekt), wenn Sie IEquatable\<t implementieren >
[CA1068](ca1068.md) | CancellationToken-Parameter müssen zuletzt aufgeführt werden.
CA1200 | Verwenden Sie keine cref-Tags mit einem Präfix.
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Literale nicht als lokalisierte Parameter übergeben.
[CA1304](ca1304-specify-cultureinfo.md) | CultureInfo angeben.
[CA1305](ca1305-specify-iformatprovider.md) | IFormatProvider angeben.
[CA1307](ca1307-specify-stringcomparison.md) | StringComparison angeben.
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Zeichenfolgen in Großbuchstaben normalisieren.
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Ordinalzeichenfolgen-Vergleich verwenden
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | P/Invokes dürfen nicht sichtbar sein.
[CA1501](ca1501-avoid-excessive-inheritance.md) | Übermäßige Vererbung vermeiden.
[CA1502](ca1502-avoid-excessive-complexity.md) | Übermäßige Komplexität vermeiden.
[CA1505](ca1505-avoid-unmaintainable-code.md) | Nicht wartbaren Code vermeiden.
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Übermäßige Klassenkopplungen vermeiden.
[CA1507](ca1507.md) | Verwenden von "nameof" zum Ausdrücken von Symbolnamen
CA1508 | Vermeiden von unzustellbaren bedingten Code
CA1509 | Ungültiger Eintrag in der Spezifikations Datei der Code Metrik
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Bezeichner sollten keine Unterstriche enthalten.
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Bezeichner sollten ein richtiges Suffix aufweisen.
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Bezeichner sollten kein falsches Suffix aufweisen.
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Keine Typnamen als Präfixe für Enumerationswerte verwenden.
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Flags-Enumerationen sollten Pluralnamen aufweisen.
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Bezeichner sollten ein korrektes Präfix aufweisen.
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Bezeichner enthält Typnamen
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Typnamen sollten nicht mit Namespaces identisch sein.
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Parameternamen sollten mit der Basisdeklaration übereinstimmen.
[CA1801](ca1801.md) | Nicht verwendete Parameter überprüfen.
[CA1802](ca1802.md) | Verwenden Sie nach Bedarf Literale.
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
CA1825 | Vermeiden Sie Array Belegungen der Länge 0 (null).
CA1826 | Verwenden Sie keine Enumerable-Methoden für indizierbare Auflistungen. Verwenden Sie stattdessen die Auflistung direkt.
[CA2000](ca2000.md) | Objekte verwerfen, bevor Bereich verloren geht.
[CA2002](ca2002.md) | Auf Objekten mit schwacher Identität nicht sperren.
[CA2007](ca2007.md) | Es empfiehlt sich, die Konfiguration für die erwartete Aufgabe zu aktivieren.
CA2008 | Erstellen Sie keine Aufgaben, ohne einen TaskScheduler zu übergeben.
CA2009 | "Nicht aufzurufende Sammlung" für einen immutablecollection-Wert
CA2010 | Verwenden Sie immer den Wert, der von mit PreserveSigAttribute markierten Methoden zurückgegeben wird.
[CA2100](ca2100.md) | SQL-Abfragen auf Sicherheitsrisiken überprüfen.
[CA2101](ca2101.md) | Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.
[CA2119](ca2119.md) | Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.
[CA2153](ca2153.md) | Beschädigte Zustands Ausnahmen nicht erfassen
[CA2200](ca2200.md) | Erneut auslösen, um Stapel Details beizubehalten.
[CA2201](ca2201.md) | Keine reservierten Ausnahmetypen auslösen.
[CA2207](ca2207.md) | Statische Felder für Werttyp inline initialisieren.
[CA2208](ca2208.md) | Argumentausnahmen korrekt instanziieren.
[CA2211](ca2211.md) | Nicht konstante Felder sollten nicht sichtbar sein.
[CA2213](ca2213.md) | Verwerfbare Felder verwerfen.
[CA2214](ca2214.md) | Überschreibbare Methoden in Konstruktoren nicht aufrufen.
[CA2216](ca2216.md) | Verwerfbare Typen sollten einen Finalizer deklarieren.
[CA2217](ca2217.md) | Enumerationen nicht mit FlagsAttribute markieren.
[CA2218](ca2218.md) | GetHashCode beim Überschreiben von Equals überschreiben.
[CA2219](ca2219.md) | Keine Ausnahmen in den Schluss Klauseln
[CA2224](ca2224.md) | Überschreiben von Gleichheits beim Überladen von Operatoren
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
CA2244 | Indizierte Element Initialisierungen nicht duplizieren
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
[CA3076](ca3076.md) | Unsichere XSLT-Skript Verarbeitung.
[CA3077](ca3077.md) | Unsichere Verarbeitung in API-Design, XmlDocument und XmlTextReader
[CA3147](ca3147.md) | Markieren von Verb Handlern mit Token zum Überprüfen der Antifälschung
[CA5350](ca5350.md) | Keine schwachen Kryptografiealgorithmen verwenden.
[CA5351](ca5351.md) | Verwenden Sie keine unterbrochenen Kryptografiealgorithmen.
CA5358 | Verwenden Sie keine unsicheren Verschlüsselungsmodi.
CA5359 | Zertifikat Überprüfung nicht deaktivieren
CA5360 | Keine gefährlichen Methoden bei der Deserialisierung aufzurufen
CA5361 | Die SChannel-Verwendung der starken Kryptografie nicht deaktivieren
CA5362 | In der serialisierbaren Klasse nicht auf sich selbst verweisen
CA5363 | Anforderungs Validierung nicht deaktivieren
CA5364 | Veraltete Sicherheitsprotokolle nicht verwenden
CA5365 | HTTP-Header Überprüfung nicht deaktivieren
CA5366 | Verwenden von XmlReader für DataSet-Lese-XML
CA5367 | Typen mit Zeiger Feldern nicht serialisieren
CA5368 | Festlegen von "VIEWSTATUS User Key" für von der Seite abgeleitete Klassen
CA5369 | XmlReader für die Deserialisierung verwenden
CA5370 | Verwenden von XmlReader zum Überprüfen des Readers
CA5371 | Verwenden von XmlReader für Schema Lesevorgänge
CA5372 | XmlReader für XPathDocument verwenden
CA5373 | Verwenden Sie keine veraltete Schlüsselableitungsfunktion.
CA5374 | XslTransform nicht verwenden
CA5375 | Konto Shared Access Signature nicht verwenden
CA5376 | Verwenden von sharedaccessproycol httpsonly
CA5377 | Zugriffs Richtlinie auf Container Ebene verwenden
CA5378 | Deaktivieren Sie ServicePointManagerSecurityProtocols nicht.
CA5379 | Algorithmus für schwache Schlüssel abderivations Funktion nicht verwenden
CA9999 | Konflikt bei der Analyzer-Version

## <a name="unported-rules"></a>Nicht portierte Regeln

Die Regeln, die nicht in [FxCop-Analysen](install-fxcop-analyzers.md) portiert wurden, bestehen aus Regeln, die noch nicht portiert wurden, aber trotzdem [portiert werden können](#rules-that-may-be-ported)und die [nicht portiert werden](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Regeln, die möglicherweise portiert werden

Die folgenden veralteten FxCop-Analyse Regeln wurden noch nicht als Analyzers implementiert, sind aber trotzdem möglich. Der Grund hierfür kann ein blockierender technischer Grund sein oder lediglich die Regel mit niedrigerer Priorität. Weitere Informationen zum Portieren-Status der einzelnen Regeln erhalten Sie, indem Sie auf den Link in der Spalte nach **Verfolgungs Problem** klicken.

Regel-ID | Nach Verfolgungs Problem
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

Die folgenden veralteten FxCop-Analyse Regeln sind veraltet und werden nicht als Analyzers implementiert. Weitere Informationen finden Sie auf der Seite mit den [GitHub-Problemen von Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port)(z. b. **CA1009**).

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

- [Microsoft. Code Analysis. fxcopanalyzers-Regeln](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
