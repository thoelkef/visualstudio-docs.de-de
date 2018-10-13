---
title: API-Referenz (Visual Studio-Debugging) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 979a6b999e34b5cec57e4a0d324f8c273fbe5dc2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222086"
---
# <a name="api-reference-visual-studio-debugging"></a>API-Referenz (Visual Studio-Debugging)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Der Referenzabschnitt enthält eine konzeptionelle Übersicht über die API, eine Anleitung, die Syntax und Verwendung für alle API-Elemente anzeigt, und eine Sammlung von Codebeispielen. Alle Verweise werden alphabetisch nach Kategorie aufgelistet.  
  
 Die folgende Tabelle zeigt die allgemeine `HRESULT` Werte, die von Methoden zurückgegeben werden.  
  
|name|Beschreibung|Wert|  
|----------|-----------------|-----------|  
|S_OK|Erfolgreich.|0x00000000|  
|E_UNEXPECTED|Unerwarteter Fehler.|0x8000ffff|  
|E_NOTIMPL|Nicht implementiert.|0 x 80004001|  
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher zum Abschließen des Vorgangs.|0x8007000E|  
|E_INVALIDARG|Ein oder mehrere Argumente sind ungültig.|0 x 80070057|  
|E_NOINTERFACE|Schnittstelle nicht unterstützt.|0 x 80004002|  
|E_POINTER|Ungültiger Zeiger.|0 x 80004003|  
|E_HANDLE|Ungültiges Handle.|0x80070006|  
|E_ABORT|Der Vorgang wurde abgebrochen.|0 x 80004004|  
|E_FAIL|Unerwarteter Fehler.|0 x 80004005|  
|E_ACCESSDENIED|Allgemeiner Zugriffsfehler.|0 x 80070005|  
  
> [!NOTE]
>  Wenn eine [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debuggen die Methode gibt `S_OK`, es wird davon ausgegangen, dass all Parameter Zeiger gültig sind, d. h. keine Überprüfung durchgeführt, auf out Parameter Zeiger beim `S_OK` zurückgegeben wird.  
  
> [!NOTE]
>  Ungültige oder `NULL` [out]-Parameter kann dazu führen, dass die IDE abstürzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

