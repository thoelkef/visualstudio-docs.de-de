---
title: Regelsatz für Sicherheitsregeln für verwalteten Code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="security-rules-rule-set-for-managed-code"></a>Regelsatz für Sicherheitsregeln für verwalteten Code
Sie sollten berücksichtigen, dass den Microsoft-Sicherheitsregeln Regelsatz, um die Anzahl der potenziellen Sicherheitsprobleme zu maximieren, die gemeldet werden.

|Regel|Beschreibung|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Überprüfen Sie die SQL-Abfragen für Sicherheitsrisiken|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Imperative Sicherheit überprüfen|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Arrayfelder dürfen nicht schreibgeschützt sein|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Sichere bestätigt|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Deny und PermitOnly überprüfen nur Auslastung|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Sichtbare Ereignishandler überprüfen|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Rufen Sie GC. Der KeepAlive beim Verwenden systemeigener Ressourcen|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Überprüfen Sie die Verwendung von SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Versiegeln-Methoden, die privater Schnittstellen erfüllen|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sichere Serialisierungskonstruktoren|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statische Konstruktoren sollten privat sein.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Umschließen anfällige finally-Klauseln mit äußerem|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern vererbungsanforderungen|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen können nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so wichtig wie Standardkonstruktoren des Basistyps sein.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Beim Überschreiben von Basismethoden eine müssen Methoden konsistente Transparenz wahren|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Elemente sollten nicht in Konflikt stehenden transparenzanmerkungen aufweisen.|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden müssen nicht mit LinkDemands erfüllen.|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Sicherheitstransparenter Code sollte nicht mit LinkDemands geschützt werden|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparente Methoden sollten keine sicherheitsanforderungen verwenden|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Sicherheitstransparenter Code sollte keine Assemblys aus Bytearrays laden.|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparente Methoden sollten nicht mit dem SuppressUnmanagedCodeSecurityAttribute ausgestattet sein.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens so wichtig wie ihre Basistypen und Schnittstellen sein.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden bestätigt|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen nicht in systemeigenen Code durchführen.|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Assemblys müssen gültige starke Namen aufweisen.|