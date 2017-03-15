---
title: "SccGetUserOption-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption-Funktion"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetUserOption-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft eine Vielzahl von benutzerspezifischen Optionen ab.  
  
## Syntax  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 nOption  
 \[in\] Option zum Abrufen \(mögliche Optionen finden Sie unter "Hinweise"\).  
  
 lpVal  
 \[out\] Option zugeordnete Wert.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Option wurde erfolgreich abgerufen.|  
|SCC\_E\_OPNOTSUPPORTED|Option wird nicht unterstützt.|  
|SCC\_E\_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## Hinweise  
 Mit diesem Befehl werden die folgenden Optionen unterstützt:  
  
|Option ' User '|Beschreibung|  
|---------------------|------------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer möchte Dateien lokale Version auszuchecken.`lpVal` erhält `SCC_USEROPT_COLV_YES` \(Benutzer möchte zum Auschecken lokaler Dateien\) oder `SCC_USEROPT_COLV_NO`.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)