---
title: "SccGetExtendedCapabilities-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetExtendedCapabilities"
helpviewer_keywords: 
  - "SccGetExtendedCapabilities-Funktion"
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccGetExtendedCapabilities-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion gibt zusätzliche Funktionen, die von dem Datenquellen\-Steuerelement\-Plug\-in unterstützt.  
  
## Syntax  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,   LPBOOL pbSupported  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 lSccExCaps  
 \[in\] Ein Flag, das eine erweiterte Funktion, die zu überprüfende angeben \(siehe die Tabelle erweiterte Funktion Code im [Capability Flags](../extensibility/capability-flags.md) für die möglichen Flags\).  
  
 pbSupported  
 \[out\] Gibt NULL zurück \(`TRUE`\), wenn die angegebene Funktion unterstützt wird; andernfalls 0 \(null\) \(`FALSE`\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Get\-Funktion\-Vorgang wurde erfolgreich abgeschlossen.|  
|SCC\_E\_UNKNOWNERROR<br /><br /> SCC\_E\_NONSPECIFICERROR|Unbekannte oder nicht angegebene Fehler ist aufgetreten.|  
  
## Hinweise  
 Diese Methode wird bei Bedarf aufgerufen. d. h., wenn eine Funktion getestet werden muss, wird diese Methode aufgerufen bestimmen, ob, die Funktion unterstützt wird. Es wird jeweils nur ein Flag angegeben.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)   
 [Capability Flags](../extensibility/capability-flags.md)