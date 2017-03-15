---
title: "API-Referenz (Visual Studio-Debugging) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], API-Referenz"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# API-Referenz (Visual Studio-Debugging)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Referenzteil umfasst grundlegende Übersicht der APIs, der Führungslinie, das die Syntax und Verwendung für alle API\-Elemente anzeigt, und der Zusammenstellung von Codebeispielen.  Alle Verweise werden alphabetisch nach Kategorie aufgelistet.  
  
 In der folgenden Tabelle werden die Common\- `HRESULT`\-Werte an, die von Methoden zurückgegeben werden.  
  
|Name|Beschreibung|Wert|  
|----------|------------------|----------|  
|S\_OK|Erfolgreich.|0x00000000|  
|E\_UNEXPECTED|Unerwarteter Fehler.|0x8000FFFF|  
|E\_NOTIMPL|Nicht implementiert.|0x80004001|  
|E\_OUTOFMEMORY|Nicht genügend Speicher zum Abschließen des Vorgangs.|0x8007000E|  
|E\_INVALIDARG|Mindestens ein Argument ist ungültig.|0x80070057|  
|E\_NOINTERFACE|Keine dieser Schnittstelle unterstützt.|0x80004002|  
|E\_POINTER|Ungültiger Zeiger.|0x80004003|  
|E\_HANDLE|Ungültiges Handle.|0x80070006|  
|E\_ABORT|Vorgang abgebrochen.|0x80004004|  
|E\_FAIL|Unerwarteter Fehler.|0x80004005|  
|E\_ACCESSDENIED|Allgemeiner Fehler Zugriff verweigert.|0x80070005|  
  
> [!NOTE]
>  Wenn eine [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugmethode `S_OK`zurückgibt, wird davon ausgegangen, dass alle out\-Parameter Zeiger gültig sind, das heißt Zeiger Out\-Parameter auf keine Validierung durchgeführt wird, wenn `S_OK` zurückgegeben wurde.  
  
> [!NOTE]
>  Ungültige oder `NULL` \[out\] Parameter kann die IDE Absturz führen.  
  
## Siehe auch  
 [Schnittstellen](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)