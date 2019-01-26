---
title: API-Referenz (Visual Studio-Debugging) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dfe0405406405dc1e09e18c49f7de7b4aecd7fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013326"
---
# <a name="api-reference-visual-studio-debugging"></a>API-Referenz (Visual Studio-Debugging)
Der Referenzabschnitt enthält eine konzeptionelle Übersicht über die API, eine Anleitung, die Syntax und Verwendung für alle API-Elemente anzeigt, und eine Sammlung von Codebeispielen. Alle Verweise werden alphabetisch nach Kategorie aufgelistet.  
  
 Die folgende Tabelle zeigt die allgemeine `HRESULT` Werte, die von Methoden zurückgegeben werden.  
  
|name|Beschreibung|Wert|  
|----------|-----------------|-----------|  
|S_OK|Erfolgreich.|0x00000000|  
|E_UNEXPECTED|Unerwarteter Fehler.|0x8000FFFF|  
|E_NOTIMPL|Nicht implementiert.|0x80004001|  
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher zum Abschließen des Vorgangs.|0x8007000E|  
|E_INVALIDARG|Ein oder mehrere Argumente sind ungültig.|0x80070057|  
|E_NOINTERFACE|Schnittstelle nicht unterstützt.|0x80004002|  
|E_POINTER|Ungültiger Zeiger.|0x80004003|  
|E_HANDLE|Ungültiges Handle.|0x80070006|  
|E_ABORT|Der Vorgang wurde abgebrochen.|0x80004004|  
|E_FAIL|Unerwarteter Fehler.|0x80004005|  
|E_ACCESSDENIED|Allgemeiner Zugriffsfehler.|0x80070005|  
  
> [!NOTE]
>  Wenn eine [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debuggen die Methode gibt `S_OK`, es wird davon ausgegangen, dass all Parameter Zeiger gültig sind, d. h. keine Überprüfung durchgeführt, auf out Parameter Zeiger beim `S_OK` zurückgegeben wird.  
> 
> [!NOTE]
>  Ungültige oder `NULL` [out]-Parameter kann dazu führen, dass die IDE abstürzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)