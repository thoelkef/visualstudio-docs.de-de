---
title: SccBackgroundGet-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2131eabd0c5933e949ab3119a89c79681f2faab1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256645"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ruft aus der quellcodeverwaltung jeder der angegebenen Dateien ohne Benutzerinteraktion ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in, out] Array der Namen von Dateien abgerufen werden sollen.  
  
> [!NOTE]
>  Die Namen müssen vollständig qualifizierten lokalen Dateinamen sein.  
  
 dwFlags  
 [in] Befehl Flags (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Ein eindeutiger Wert, der diesen Vorgang zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang erfolgreich abgeschlossen wurde.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Hintergrund Abruf wird bereits ausgeführt (das Quellcodeverwaltungs-Plug-in sollte dies nur zurück, wenn es keine gleichzeitigen Batchvorgänge unterstützt).|  
|SCC_I_OPERATIONCANCELED|Vorgang wurde abgebrochen, bevor Sie abgeschlossen wird.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird immer in einem anderen Thread aufgerufen, die das Quellcodeverwaltungs-Plug-In geladen wird. Diese Funktion wird nicht erwartet, zurückgegeben werden, bis er abgeschlossen ist; Allerdings kann es mehrere Male mit mehreren Listen von Dateien, alle gleichzeitig aufgerufen werden.  
  
 Die Verwendung der `dwFlags` Argument ist identisch mit der [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

