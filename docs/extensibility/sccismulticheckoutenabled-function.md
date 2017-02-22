---
title: "SccIsMultiCheckoutEnabled-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccIsMultiCheckoutEnabled"
helpviewer_keywords: 
  - "SccIsMultiCheckoutEnabled-Funktion"
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccIsMultiCheckoutEnabled-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion prüft, ob das Quellcodeverwaltungs\-Plug\-in Mehrfaches Auschecken einer Datei ermöglicht.  
  
## Syntax  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 pbMultiCheckout  
 \[out\] Gibt an, ob Mehrfaches für dieses Projekt \(ungleich NULL bedeutet, dass Mehrfaches Auschecken unterstützt werden\) aktiviert sind.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Überprüfung war erfolgreich.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Die IDE stellt zwei prüft, ob mehrere Benutzer gleichzeitig Dateien ausgecheckt werden können. Zuerst muss das Quellcodeverwaltungssystem Mehrfaches unterstützen. Das Quellcodeverwaltungs\-Plug\-in kann diese Funktion während der Initialisierung angeben, durch Angabe der `SCC_CAP_MULTICHECKOUT`. Die IDE ruft anschließend eine zweite Überprüfung, dieser Funktion können Sie bestimmen, ob das aktuelle Projekt Mehrfaches unterstützt. Wenn Mehrfaches Auschecken für das ausgewählte Projekt unterstützt werden, gibt Erfolg\-Plug\-in code und legt `pbMultiCheckout` auf einen Wert ungleich Null \(`TRUE`\) oder `FALSE`.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)