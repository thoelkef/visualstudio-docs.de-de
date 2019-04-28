---
title: Interoperabilitätswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68ea8c66b26ee2463969ca71b8f0e5ac78b3f0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823594"
---
# <a name="interoperability-warnings"></a>Interoperabilitätswarnungen

Interoperabilitätswarnungen unterstützt die Interaktion mit COM-Clients.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1400: P/Invoke-Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) | Eine öffentliche oder geschützte Methode wird mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut markiert. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. |
| [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Eine öffentliche oder geschützte Methode in ein öffentlicher Typ hat das System.Runtime.InteropServices.DllImportAttribute-Attribut (auch durch das Schlüsselwort "Declare" in Visual Basic implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| [CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem dem Namen ein Unterstrich (_) und eine ganze Zahl angefügt werden, die der Reihenfolge der Deklaration der Überladung entspricht. |
| [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | Ein für COM sichtbarer Werttyp wird mit dem auf LayoutKind.Auto festgelegten System.Runtime.InteropServices.StructLayoutAttribute-Attribut markiert. Das Layout dieser Typen kann zwischen Versionen von .NET Framework ändern, die COM-Clients unterbrochen wird, die ein bestimmtes Layout erwarten. |
| [CA1404: GetLastError unmittelbar nach P/Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Wird aufgerufen, GetLastWin32Error-Methode oder einer entsprechenden [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError-Funktion, und der unmittelbar vorherige Aufruf ist nicht auf einer Plattform invoke-Methode. |
| [CA1405: COM sichtbare Basistypen sollten für COM sichtbar sein](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | Ein für COM sichtbarer Typ wird von einem Typ abgeleitet, der nicht für COM sichtbar ist. |
| [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen. |
| [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM unterstützt keine statischen Methoden. |
| [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. Standardmäßig wird eine auf Dispatch beschränkte Schnittstelle verwendet, wenn das ClassInterfaceAttribute-Attribut nicht angegeben wird. |
| [CA1409: Für COM sichtbare Typen müssen erstellt werden können.](../code-quality/ca1409-com-visible-types-should-be-creatable.md) | Ein Verweistyp, der speziell als für COM sichtbar gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, jedoch keinen öffentlichen (parameterlosen) Standardkonstruktor. Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht von COM-Clients erstellt werden. |
| [CA1410: COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Ein Typ deklariert eine Methode, die mithilfe von markiert ist die <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut deklariert jedoch keine Methode, die mithilfe von markiert ist die <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut, oder umgekehrt. |
| [CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | Eine Methode, die mit dem System.Runtime.InteropServices.ComRegisterFunctionAttribute-Attribut oder dem System.Runtime.InteropServices.ComUnregisterFunctionAttribute-Attribut markiert ist, ist extern sichtbar. |
| [CA1412: ComSource-Schnittstellen als IDispatch markieren](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | Ein Typ ist mit dem System.Runtime.InteropServices.ComSourceInterfacesAttribute-Attribut markiert, und mindestens eine der angegebenen Schnittstellen ist nicht mit dem auf ComInterfaceType.InterfaceIsIDispatch festgelegten System.Runtime.InteropServices.InterfaceTypeAttribute-Attribut markiert. |
| [CA1413: Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt der Felder auf Informationen, die nicht verfügbar gemacht werden sollen oder unbeabsichtigte Auswirkungen auf Design oder Sicherheit haben. |
| [CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Der boolesche Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. |
| [CA1415: P/Invokes korrekt deklarieren](../code-quality/ca1415-declare-p-invokes-correctly.md) | Diese Regel sucht für Plattformaufrufdeklarationen Methode, die auf [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Funktionen, die einen Zeiger auf einen OVERLAPPED-Strukturparameter und der zugehörige verwaltete Parameter ist nicht als ein Zeiger auf eine <xref:System.Threading.NativeOverlapped?displayProperty=fullName> Struktur. |