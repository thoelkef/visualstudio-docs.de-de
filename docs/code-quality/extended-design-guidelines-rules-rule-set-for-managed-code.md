---
title: "Erweiterte Regelsatz Entwurfsrichtlinienregeln für verwalteten Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cdba59674b53f82707a586aa3f94695666db695e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Regelsatz für die erweiterten Entwurfsrichtlinienregeln für verwalteten Code
Der Regelsatz Microsoft erweiterten Entwurfsrichtlinienregeln erweitert die einfachen Entwurfsrichtlinienregeln bezüglich Verwendbarkeit und wartbarkeit und maximieren die gemeldeten. Besonderes Augenmerk wird auf Benennungsrichtlinien gelegt. Sie sollten diesen Regelsatz Wenn Ihr Projekt Bibliothekscode umfasst oder wenn Sie höchste Standards für das Schreiben von Code, der leicht zu warten ist erzwingen möchten.  
  
 Die erweiterten Entwurfsrichtlinienregeln umfassen alle von der Microsoft grundlegenden Regeln für Entwurfsrichtlinien. Die grundlegenden Regeln für Entwurfsrichtlinien umfassen alle Microsoft-Mindestregeln. Weitere Informationen finden Sie unter [Regelsatz einfachen Entwurfsrichtlinienregeln für verwalteten Code](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) und [Regelsatz für verwaltete empfohlene Regeln für verwalteten Code](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 Die folgende Tabelle beschreibt alle Regeln im Regelsatz Microsoft erweiterten Entwurfsrichtlinienregeln.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Ereignishandler korrekt deklarieren|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Assemblys mit AssemblyVersionAttribute markieren|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Verschieben von P/Invokes in NativeMethods-Klasse|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Basisklassenmethoden nicht ausblenden|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable korrekt implementieren|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke-Einstiegspunkte vorhanden sein|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes dürfen nicht sichtbar sein.|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Rufen Sie GetLastError unmittelbar nach P/Invoke aufrufen|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM sichtbare Basistypen sollten für COM sichtbar sein|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM-Registrierungsmethoden müssen übereinstimmen|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes korrekt deklarieren|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Werttypfelder sollten portabel sein.|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarationen von P/Invoke müssen portabel sein|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Auf Objekten mit schwacher Identität nicht sperren|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Überprüfen Sie die SQL-Abfragen für Sicherheitsrisiken|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Festlegen Sie Marshalling für P/Invoke-Zeichenfolgenargumente|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Umschließen anfällige finally-Klauseln mit äußerem|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern vererbungsanforderungen|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen können nicht an Typäquivalenz beteiligt sein.|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so wichtig wie Standardkonstruktoren des Basistyps sein.|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden.|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Beim Überschreiben von Basismethoden eine müssen Methoden konsistente Transparenz wahren|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden müssen nicht mit LinkDemands erfüllen.|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens so wichtig wie ihre Basistypen und Schnittstellen sein.|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden bestätigt|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen nicht in systemeigenen Code durchführen.|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Erneut ausführen, um Stapeldetails beizubehalten|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Objekte nicht mehrmals verwerfen|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Statische Felder Werttyp Inline initialisieren|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nicht verarbeitete Komponenten mit WebMethod markieren|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen sollten verworfen werden.|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Verwerfbare Typen sollten einen Finalizer deklarieren|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serialisierungskonstruktoren implementieren|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen des Gleichheitsoperators beim Überschreiben von ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Markieren von Windows Forms-Einstiegspunkte mit STAThread markieren|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Alle nicht serialisierbaren Felder markieren|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Rufen Sie Basisklassenmethoden auf ISerializable-Typen|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Markieren von ISerializable-Typen mit SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serialisierungsmethoden korrekt implementieren|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable ordnungsgemäß implementieren|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Geben Sie die richtigen Argumente für Formatierungsmethoden angeben|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Ordnungsgemäß auf NaN testen|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Statische Member in generischen Typen nicht deklarieren|  
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Generische Listen nicht verfügbar machen|  
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Generische Ereignishandlerinstanzen verwenden|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Generische Methoden müssen den Typparameter angeben.|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Vermeiden Sie übermäßige Anzahl von Parametern in generischen Typen|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Generische Typen in Membersignaturen nicht schachteln|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Verwenden Sie Generika|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|-Enumerationen sollten Nullwert aufweisen.|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Auflistungen müssen eine generische Schnittstelle implementieren|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Betrachten Sie Basistypen als Parameter übergeben.|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Abstrakte Typen dürfen keine Konstruktoren aufweisen.|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Assemblys mit CLSCompliantAttribute markieren|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Assemblys mit ComVisibleAttribute markieren|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Attribute mit AttributeUsageAttribute markieren|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Accessors für Attributargumente definieren|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indexer sollten nicht mehrdimensional sein.|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Verwenden Sie Eigenschaften aus, falls zutreffend|  
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Sich wiederholende Argumente durch ein Parameterarray ersetzen|  
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Standardparameter sollten nicht verwendet werden|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Enumerationen mit FlagsAttribute markieren|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Enumerationsspeicher sollte Int32 sein.|  
|[CA1030 NACH MÖGLICHKEIT](../code-quality/ca1030-use-events-where-appropriate.md)|Verwenden Sie Ereignisse|  
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Allgemeine Ausnahmetypen nicht auffangen|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standardausnahmekonstruktoren implementieren|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Geschachtelte Typen sollten nicht sichtbar sein.|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection-Implementierungen haben Member mit starker Typisierung|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Methoden bei vergleichbaren Typen überschreiben|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Enumeratoren sollten eine starke Typisierung werden|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listen sind stark typisiert.|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute-Meldung|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Eigenschaften sollten nicht lesegeschützt sein.|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Gleichheitsoperator für Referenztypen nicht überladen|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Geschützte Member in versiegelten Typen nicht deklarieren|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Virtuelle Member in versiegelten Typen nicht deklarieren|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Deklarieren von Typen in namespaces|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Sichtbare Instanzfelder nicht deklarieren|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statische Haltertypen sollten versiegelt sein|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statische Haltertypen sollten keine Konstruktoren aufweisen.|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI-Parameter dürfen keine Zeichenfolgen sein.|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI-Rückgabewerte sollten keine Zeichenfolgen sein|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|URI-Überladungen String rufen Überladungen vom System.Uri auf|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typen sollten bestimmte Basistypen nicht erweitern.|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Member sollten bestimmte konkreten Typen nicht verfügbar machen|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Ausnahmen sollten öffentlich sein.|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Variablennamen sollten nicht mit Feldnamen übereinstimmen.|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Übermäßige Komplexität vermeiden|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Bezeichner sollte durch die Groß-/Kleinschreibung unterscheiden.|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Bezeichner dürfen nicht mit Schlüsselwörtern übereinstimmen.|  
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Nicht verwendete Parameter überprüfen|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Nicht verwendete lokale Variablen entfernen|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Übermäßige lokale Variablen vermeiden|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Statische Felder von Verweistypen Inline initialisieren|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Nicht aufgerufenen privaten Code vermeiden|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Nicht instanziierte interne Klassen vermeiden|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Nicht versiegelte Attribute vermeiden|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Ziehen Sie verzweigte Arrays mehrdimensionalen|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Außerkraftsetzung equals und Gleichheitsoperator für Werttypen|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Eigenschaften sollten keine Arrays zurückgeben.|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Member als statisch markieren|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Nicht verwendete private Felder vermeiden|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Keine reservierten Ausnahmetypen auslösen|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Verwenden Sie die verwaltete Entsprechungen der Win32-API|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Argumentausnahmen korrekt instanziieren|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Nicht konstante Felder sollten nicht sichtbar sein.|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nicht Enumerationen mit FlagsAttribute markieren|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Keine Ausnahmen in Ausnahmeklauseln auslösen|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizer sollten geschützt sein|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Sichtbarkeit für geerbte Member nicht verringern|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Member sollten sich durch mehr als den Rückgabetyp unterscheiden.|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Außerkraftsetzung equals beim Überladen des Gleichheitsoperators|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operatorüberladungen weisen benannte alternativen auf|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatoren sollten symmetrische Überladungen aufweisen.|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Auflistungseigenschaften sollten schreibgeschützt sein|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Params für Variablenargumente verwenden|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Deserialisierungsmethoden für optionale Felder angeben|  
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Namespaces mit wenigen Typen vermeiden|  
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Out-Parameter vermeiden|  
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Leere Schnittstellen vermeiden|  
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Typen nicht als Verweis übergeben|  
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Argumente von öffentlichen Methoden validieren|  
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Übermäßige Vererbung vermeiden|  
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Irreführende Feldnamen überprüfen|  
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Nicht wartbaren Code vermeiden|  
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Übermäßige Klassenkopplungen vermeiden|  
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Enumerationswerte nicht mit "Reserviert" benennen|  
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden|  
|[CA1702 BEI ZUSAMMENGESETZTEN BEGRIFFEN](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Bei zusammengesetzten Begriffen sollte beachtet werden|  
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Ressourcenzeichenfolgen sollten korrekt geschrieben werden|  
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Bezeichner sollten korrekt geschrieben werden|  
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Bezeichner sollten keine Unterstriche enthalten.|  
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Bezeichner sollten korrekt Groß-/Kleinschreibung beachtet werden|  
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Bezeichner sollten ein richtiges Suffix aufweisen|  
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Bezeichner sollten kein falsches Suffix aufweisen.|  
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Die Enumerationswerte mit Typnamen kein Präfix vor|  
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Ereignisse sollten kein Before- oder after-Präfix aufweisen.|  
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Flags-Enumerationen sollten Pluralnamen aufweisen.|  
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Bezeichner sollten ein korrektes Präfix aufweisen|  
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.|  
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Parameternamen sollten nicht mit Membernamen übereinstimmen.|  
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Bezeichner dürfen keine Typnamen enthalten.|  
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.|  
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Bezeichner sollten kein falsches Präfix aufweisen.|  
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Typnamen sollten nicht mit Namespaces übereinstimmen.|  
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Parameternamen sollten mit der Basisdeklaration übereinstimmen|  
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Bevorzugte Begriffe verwenden|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Literale sollten korrekt geschrieben werden|