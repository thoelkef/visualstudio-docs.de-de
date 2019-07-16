---
title: SccUninitialize-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190848"
---
# <a name="sccuninitialize-function"></a>SccUninitialize-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion löscht alle Zuordnungen oder offene Verbindungen, die von einem vorherigen Aufruf von erstellt die [SccInitialize](../extensibility/sccinitialize-function.md) als Vorbereitung für das Quellcodeverwaltungs-Plug-in wird heruntergefahren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Der Zeiger auf die Datenquellen-Steuerelement-Plug-in Context-Struktur erstellt, der [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|  
  
## <a name="remarks"></a>Hinweise  
 Das Quellcodeverwaltungs-Plug-in ist verantwortlich für die Vorbereitung heruntergefahren werden, und Freigeben von Arbeitsspeicher, die das plug-in für die Context-Struktur zugeordnet ist. Die Funktion wird einmal für jede bestimmte Instanz eines Plug-Ins aufgerufen. Ein Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md) dieses Aufrufs steht. Keine Projekte können immer noch geöffnet sein zum Zeitpunkt des Aufrufs von `SccUninitialize`.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
