---
title: Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 000b1780b0124d579ed0b9481c7d18966663ca51
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987313"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code
Der Regelsatz Microsoft erweiterte Regeln für Richtigkeit maximiert die Logik und Fehler, die von der Codeanalyse gemeldet werden. Besonderes Augenmerk wird auf bestimmte Szenarien wie z. B. COM-Interoperabilität und mobile Anwendungen. Sie sollten diesen Regelsatz, wenn eines dieser Szenarien zutrifft, zu Ihrem Projekt oder um weitere Probleme in Ihrem Projekt zu ermitteln.

 Der erweiterte Microsoft-Regeln für Richtigkeit Regelsatz umfasst die Regeln, die in der Regel Microsoft grundlegenden Regeln für Richtigkeit festgelegt werden. Die grundlegenden Regeln für Richtigkeit enthalten die Regeln, die in der Microsoft-Mindestregeln Regel festgelegt werden. Weitere Informationen finden Sie unter [Regelsatz grundlegenden Regeln für Richtigkeit für verwalteten Code](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) und [Regelsatz für verwaltete empfohlene Regeln für verwalteten Code](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 Die folgende Tabelle beschreibt alle Regeln im Regelsatz Microsoft erweiterte Regeln für Richtigkeit.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Ereignishandler korrekt deklarieren|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Assemblys mit AssemblyVersionAttribute markieren|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typen, die systemeigene Ressourcen besitzen müssen gelöscht werden können.|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Verschieben von P/Invokes in NativeMethods-Klasse|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Basisklassenmethoden nicht ausblenden|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable korrekt implementieren|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke-Einstiegspunkte vorhanden sein|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|GetLastError unmittelbar nach P/Invoke aufrufen|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM sichtbare Basistypen sollten für COM sichtbar sein|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes korrekt deklarieren|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarationen von P/Invoke müssen portabel sein|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Klicken Sie auf Objekten mit schwacher Identität nicht sperren|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Überprüfen Sie die SQL-Abfragen für Sicherheitsrisiken|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Anfällige finally-Klauseln mit äußerem try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern vererbungsanforderungen|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens genauso kritisch sein wie die Standardkonstruktoren des Basistyps sein.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methoden müssen beim Überschreiben von Basismethoden konsistente Transparenz wahren|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen nicht Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code muss nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden dürfen keine LinkDemands erfüllen.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen sein.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden Assert-Vorgänge|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen nicht in systemeigenen Code aufrufen.|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Erneut ausführen Sie, um Stapeldetails beizubehalten|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Objekte nicht mehrmals verwerfen|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Statische Felder Werttyp Inline initialisieren|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nicht verarbeitete Komponenten mit WebMethod markieren|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Verwerfbare Typen sollten einen Finalizer deklarieren|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serialisierungskonstruktoren implementieren|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen des Gleichheitsoperators beim Überschreiben von ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Mark Windows Forms-Einstiegspunkte mit STAThread markieren|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Alle nicht serialisierbaren Felder markieren|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Aufrufen von Basisklassenmethoden auf ISerializable-Typen|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Markieren von ISerializable-Typen mit SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serialisierungsmethoden korrekt implementieren|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable ordnungsgemäß implementieren|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Geben Sie Argumente für Formatierungsmethoden angeben|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Ordnungsgemäß auf NaN testen|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|-Enumerationen sollten NULL-Wert aufweisen.|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Literale nicht als lokalisierte Parameter übergeben|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen in Großbuchstaben normalisieren|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Methodenergebnisse nicht ignorieren|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Rufen Sie GC. SuppressFinalize ordnungsgemäß|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Nur API aus Zielframework verwenden|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Entfernen Sie Aufrufe von GC. KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|SafeHandle verwenden, um systemeigene Ressourcen zu kapseln|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Arrayfelder dürfen nicht schreibgeschützt sein|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Sichere Bestätigungen|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Rufen Sie GC. KeepAlive beim Verwenden systemeigener Ressourcen|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Versiegeln Sie Methoden, private Schnittstellen erfüllen|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sichere Serialisierungskonstruktoren|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statische Konstruktoren sollten privat sein.|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Verwenden Sie verwaltete Entsprechungen der Win32-API|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizer sollten geschützt sein|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Sichtbarkeit für geerbte Member nicht verringern|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Member sollten sich durch mehr als den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Außerkraftsetzung equals, Equals beim Überladen|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Sammlungseigenschaften sollten schreibgeschützt sein|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Deserialisierungsmethoden für optionale Felder angeben|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standardausnahmekonstruktoren implementieren|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI-Rückgabewerte sollten keine Zeichenfolgen sein|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Überladungen in für COM sichtbaren Schnittstellen vermeiden|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Int64-Argumente für Visual Basic 6-Clients vermeiden|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Statische Member in für COM sichtbaren Typen vermeiden|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|AutoDual ClassInterfaceType nicht verwenden|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Für COM sichtbare Typen müssen erstellt werden können.|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|COM-Registrierungsmethoden dürfen nicht sichtbar sein.|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource-Schnittstellen als IDispatch markieren|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Boolesche P/Invoke-Argumente mit MarshalAs markieren|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Verwenden Sie nicht im Leerlauf Prozesse mit der Priorität|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Verwenden Sie keine Timer, die Änderungen am Betriebszustand zu verhindern.|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Assemblys mit NeutralResourcesLanguageAttribute markieren|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Keine problematischen Methoden aufrufen|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Fibers nicht als Threads behandeln|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Member dürfen keine in Konflikt stehenden transparenzanmerkungen aufweisen.|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparenter Code darf nicht mit LinkDemands geschützt werden|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparente Methoden dürfen keine sicherheitsanforderungen verwenden.|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparenter Code darf keine Assemblys aus Bytearrays laden|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity versehen werden|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Literale sollten eine korrekte Rechtschreibung aufweisen|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nicht Enumerationen mit FlagsAttribute markieren|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Überschreiben von GetHashCode beim Überschreiben von Equals überschreiben|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Keine Ausnahmen in Ausnahmeklauseln auslösen|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operatorüberladungen weisen benannte alternativen auf|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Führen Sie nicht freigegebene Ressourcenformate|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Params für Variablenargumente verwenden|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Vorgänge sollten nicht überlaufen|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Attribute-Zeichenfolgenliterale müssen stets richtig analysiert|