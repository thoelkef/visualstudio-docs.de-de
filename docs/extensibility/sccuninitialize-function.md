---
title: SccUninitialize Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 434987489feccd5f576e04d69afbb4b39e1dc754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccuninitialize-function"></a>SccUninitialize-Funktion
Diese Funktion werden alle Zuweisungen oder geöffneten Verbindungen, die von einem vorherigen Aufruf erstellt bereinigt die [SccInitialize](../extensibility/sccinitialize-function.md) als Vorbereitung für das Herunterfahren der Datenquellen-Steuerelement-Plug-in.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Der Zeiger auf die Datenquellen-Steuerelement-Plug-in Context-Struktur erstellt, der [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|  
  
## <a name="remarks"></a>Hinweise  
 Die Datenquellen-Steuerelement-Plug-in ist verantwortlich für heruntergefahren werden, Vorbereiten und Freigeben von Arbeitsspeicher, die das plug-in für die Kontextstruktur zugeordnet sind. Die Funktion wird einmal für jede bestimmte Instanz eines Plug-Ins aufgerufen werden. Ein Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md) dieser Aufruf vorausgeht. Keine Projekte können immer noch geöffnet sein zum Zeitpunkt des Aufrufs von `SccUninitialize`.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)