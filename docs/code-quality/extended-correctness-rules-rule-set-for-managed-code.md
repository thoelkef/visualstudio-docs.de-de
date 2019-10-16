---
title: Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 96a0b43e6d300d3db425cb7a926d0196566d178b
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349641"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code

Der Regelsatz für erweiterte Richtigkeit von Regeln von Microsoft maximiert die Fehler bei der Logik-und frameworkverwendung, die von der Code Analyse gemeldet werden. Zusätzlicher Schwerpunkt liegt auf bestimmten Szenarien, wie z. b. com-Interoperabilität und mobilen Anwendungen. Sie sollten diesen Regelsatz einschließen, wenn eines dieser Szenarien auf Ihr Projekt zutrifft, oder um weitere Probleme in Ihrem Projekt zu finden.

Der Regelsatz für die erweiterten Regeln für Richtigkeit von Microsoft enthält die Regeln, die im Regelsatz [grundlegender Regeln](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) für die Richtigkeit von Regeln enthalten sind, der die Regeln im Regelsatz für [verwaltete Empfohlene Regeln](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) enthält.

In der folgenden Tabelle werden alle Regeln im Regelsatz für erweiterte Regeln für Richtigkeit von Microsoft beschrieben.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Ereignishandler korrekt deklarieren.|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable korrekt implementieren.|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes korrekt deklarieren.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarationen von P/Invoke müssen portabel sein.|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Auf Objekten mit schwacher Identität nicht sperren.|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2200](../code-quality/ca2200.md)|Erneut ausführen, um Stapeldetails beizubehalten.|
|[CA2202](../code-quality/ca2202.md)|Objekte nicht mehrmals verwerfen.|
|[CA2207](../code-quality/ca2207.md)|Statische Felder für Werttyp inline initialisieren.|
|[CA2212](../code-quality/ca2212.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2214](../code-quality/ca2214.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](../code-quality/ca2216.md)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2220](../code-quality/ca2220.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](../code-quality/ca2229.md)|Serialisierungskonstruktoren implementieren.|
|[CA2231](../code-quality/ca2231.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2235](../code-quality/ca2235.md)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](../code-quality/ca2237.md)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2240](../code-quality/ca2240.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](../code-quality/ca2241.md)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](../code-quality/ca2242.md)|Ordnungsgemäß auf NaN testen.|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1806](../code-quality/ca1806.md)|Methodenergebnisse nicht ignorieren.|
|[CA1816](../code-quality/ca1816.md)|GC.SuppressFinalize korrekt aufrufen.|
|[CA1819](../code-quality/ca1819.md)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](../code-quality/ca1820.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Nur API aus Zielframework verwenden.|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Aufrufe an GC.KeepAlive entfernen.|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|SafeHandle verwenden, um native Ressourcen zu kapseln.|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren.|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Arrayfelder dürfen nicht schreibgeschützt sein.|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Sichere Bestätigungen.|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sichere Serialisierungskonstruktoren.|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statische Konstruktoren sollten privat sein.|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2205](../code-quality/ca2205.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2215](../code-quality/ca2215.md)|Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.|
|[CA2221](../code-quality/ca2221.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2226](../code-quality/ca2226.md)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](../code-quality/ca2227.md)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2239](../code-quality/ca2239.md)|Deserialisierungsmethoden für optionale Felder angeben.|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standardausnahmekonstruktoren implementieren.|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI-Rückgabewerte dürfen keine Zeichenfolgen sein.|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Überladungen in für COM sichtbaren Schnittstellen vermeiden.|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Int64-Argumente für Visual Basic 6-Clients vermeiden.|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Statische Member in für COM sichtbaren Typen vermeiden.|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|AutoDual ClassInterfaceType nicht verwenden.|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Für COM sichtbare Typen müssen erstellt werden können.|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource-Schnittstellen als IDispatch markieren.|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Boolesche P/Invoke-Argumente mit MarshalAs markieren.|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Verwenden Sie keine Prozesse mit der Priorität "idle".|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern.|
|[CA1824](../code-quality/ca1824.md)|Assemblys mit NeutralResourcesLanguageAttribute markieren.|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Keine problematischen Methoden aufrufen.|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Fibers nicht als Threads behandeln.|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparenter Code darf nicht mit LinkDemands geschützt werden.|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparenter Code darf keine Assemblys aus Bytearrays laden.|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden.|
|[CA2204](../code-quality/ca2204.md)|Literale sollten eine korrekte Rechtschreibung aufweisen.|
|[CA2211](../code-quality/ca2211.md)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2217](../code-quality/ca2217.md)|Enumerationen nicht mit FlagsAttribute markieren.|
|[CA2218](../code-quality/ca2218.md)|GetHashCode beim Überschreiben von Equals überschreiben.|
|[CA2219](../code-quality/ca2219.md)|Keine Ausnahmen in Ausnahmeklauseln auslösen.|
|[CA2225](../code-quality/ca2225.md)|Operatorüberladungen weisen benannte Alternativen auf.|
|[CA2228](../code-quality/ca2228.md)|Nicht freigegebene Ressourcenformate nicht veröffentlichen.|
|[CA2230](../code-quality/ca2230.md)|params für Variablenargumente verwenden.|
|[CA2233](../code-quality/ca2233.md)|Vorgänge sollten nicht überlaufen.|
|[CA2234](../code-quality/ca2234.md)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.|
|[CA2243](../code-quality/ca2243.md)|Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.|