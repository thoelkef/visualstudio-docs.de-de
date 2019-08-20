---
title: Regelsatz für Sicherheitsregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1131f9cf0e77fd4fe68e4bc5c033491aa6dd34e1
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585192"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Regelsatz für Sicherheitsregeln für verwalteten Code

Verwenden Sie den Microsoft-Regelsatz für Sicherheitsregeln für die Legacy Code Analyse, um die Anzahl potenzieller Sicherheitsprobleme zu maximieren, die gemeldet werden.

|Regel|Beschreibung|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Imperative Sicherheit überprüfen.|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren.|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Arrayfelder dürfen nicht schreibgeschützt sein.|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Sichere Bestätigungen.|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Verwendung von Deny und PermitOnly überprüfen.|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Sichtbare Ereignishandler überprüfen.|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen.|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sichere Serialisierungskonstruktoren.|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statische Konstruktoren sollten privat sein.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparenter Code darf nicht mit LinkDemands geschützt werden.|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparenter Code darf keine Assemblys aus Bytearrays laden.|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Assemblys müssen gültige starke Namen aufweisen.|
|[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)|Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden|
|[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)|BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen|
|[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)|Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen|
|[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md)|Unsicheren Deserialisierer nicht verwenden: LosFormatter|
|[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)|Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer|
|[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)|Nicht deserialisieren, ohne zuerst NetDataContractSerializer.Binder festzulegen|
|[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)|Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist|
|[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md)|Unsicheren Deserialisierer nicht verwenden: ObjectStateFormatter|
|[CA2321](ca2321.md)|Nicht mit JavaScriptSerializer und SimpleTypeResolver deserialisieren|
|[CA2322](ca2322.md)|Vor dem Deserialisieren sicherstellen, dass JavaScriptSerializer nicht mit SimpleTypeResolver initialisiert ist|
|[CA3001](../code-quality/ca3001-review-code-for-sql-injection-vulnerabilities.md)|Review code for SQL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von SQL-Befehlen)|
|[CA3002](../code-quality/ca3002-review-code-for-xss-vulnerabilities.md)|Review code for XSS vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch XSS)|
|[CA3003](../code-quality/ca3003-review-code-for-file-path-injection-vulnerabilities.md)|Review code for file path injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen über einen Dateipfad)|
|[CA3004](../code-quality/ca3004-review-code-for-information-disclosure-vulnerabilities.md)|Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)|
|[CA3005](../code-quality/ca3005-review-code-for-ldap-injection-vulnerabilities.md)|Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)|
|[CA3006](../code-quality/ca3006-review-code-for-process-command-injection-vulnerabilities.md)|Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)|
|[CA3007](../code-quality/ca3007-review-code-for-open-redirect-vulnerabilities.md)|Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)|
|[CA3008](../code-quality/ca3008-review-code-for-xpath-injection-vulnerabilities.md)|Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)|
|[CA3009](../code-quality/ca3009-review-code-for-xml-injection-vulnerabilities.md)|Review code for XML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XML-Befehlen)|
|[CA3010](../code-quality/ca3010-review-code-for-xaml-injection-vulnerabilities.md)|Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)|
|[CA3011](../code-quality/ca3011-review-code-for-dll-injection-vulnerabilities.md)|Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)|
|[CA3012](../code-quality/ca3012-review-code-for-regex-injection-vulnerabilities.md)|Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)|
