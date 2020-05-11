---
title: API-Referenz (Visual Studio-Debugging) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738180"
---
# <a name="api-reference-visual-studio-debugging"></a>API-Referenz (Visual Studio-Debugging)
Der Verweisabschnitt enthält eine konzeptionelle Übersicht über die API, ein Handbuch, das die Syntax und Verwendung für alle API-Elemente anzeigt, sowie eine Reihe von Codebeispielen. Alle Referenzen werden alphabetisch nach Kategorie aufgelistet.

 Die folgende Tabelle `HRESULT` zeigt die allgemeinen Werte, die von Methoden zurückgegeben werden.

|Name|BESCHREIBUNG|Wert|
|----------|-----------------|-----------|
|S_OK|Erfolg.|0x00000000|
|E_UNEXPECTED|Unerwarteter Fehler.|0x8000FFFF|
|E_NOTIMPL|Nicht implementiert.|0x80004001|
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher, um den Vorgang abzuschließen.|0x8007000E|
|E_INVALIDARG|Mindestens ein Argument ist ungültig.|0x80070057|
|E_NOINTERFACE|Eine solche Schnittstelle wird nicht unterstützt.|0x80004002|
|E_POINTER|Ungültiger Zeiger.|0x80004003|
|E_HANDLE|Ungültiges Handle.|0x80070006|
|E_ABORT|Der Vorgang wurde abgebrochen.|0x80004004|
|E_FAIL|Unerwarteter Fehler.|0x80004005|
|E_ACCESSDENIED|Allgemeiner Zugriff verweigert Fehler.|0x80070005|

> [!NOTE]
> Wenn [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] eine Debuggingmethode zurückgegeben `S_OK`wird, wird davon ausgegangen, dass alle out-Parameterzeiger gültig sind, `S_OK` d. h., bei der Rückgabe wird keine Validierung für Out-Parameterzeiger durchgeführt.
>
> [!NOTE]
> Ungültige `NULL` oder [out]-Parameter können dazu führen, dass die IDE abstürzt.

## <a name="see-also"></a>Weitere Informationen
- [Schnittstellen](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
