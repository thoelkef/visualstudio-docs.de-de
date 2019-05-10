---
title: API-Referenz (Visual Studio-Debugging) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e95200cf29c8561798c858635c3864d635fb40
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424514"
---
# <a name="api-reference-visual-studio-debugging"></a>API-Referenz (Visual Studio-Debugging)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Der Referenzabschnitt enthält eine konzeptionelle Übersicht über die API, eine Anleitung, die Syntax und Verwendung für alle API-Elemente anzeigt, und eine Sammlung von Codebeispielen. Alle Verweise werden alphabetisch nach Kategorie aufgelistet.  
  
 Die folgende Tabelle zeigt die allgemeine `HRESULT` Werte, die von Methoden zurückgegeben werden.  
  
|Name|Beschreibung|Wert|  
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
> Wenn eine [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debuggen die Methode gibt `S_OK`, es wird davon ausgegangen, dass all Parameter Zeiger gültig sind, d. h. keine Überprüfung durchgeführt, auf out Parameter Zeiger beim `S_OK` zurückgegeben wird.  
  
> [!NOTE]
> Ungültige oder `NULL` [out]-Parameter kann dazu führen, dass die IDE abstürzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
