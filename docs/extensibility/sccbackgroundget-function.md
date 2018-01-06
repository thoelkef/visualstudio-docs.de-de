---
title: SccBackgroundGet Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBackgroundGet
helpviewer_keywords: SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b63a7e8c9a6b2a4f2539cd6a8426ba9df365ab76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet-Funktion
Diese Funktion ruft aus der quellcodeverwaltung jedes der angegebenen Dateien ohne Benutzerinteraktion ab.  
  
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
 [in] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 [in, out] Array der Namen der Dateien abgerufen werden sollen.  
  
> [!NOTE]
>  Die Namen müssen den vollqualifizierten lokalen Dateinamen sein.  
  
 dwFlags  
 [in] Befehl Flags (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Ein eindeutiger Wert, der diesen Vorgang zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang wurde erfolgreich abgeschlossen.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Hintergrund Abruf wird bereits ausgeführt (das Quellsteuerelement-Plug-in sollte dies nur zurück, wenn es anderen Batch-Vorgänge nicht unterstützt).|  
|SCC_I_OPERATIONCANCELED|Vorgang wurde abgebrochen, bevor Sie abgeschlossen werden kann.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird immer in einem anderen als dem Thread aufgerufen werden, die der quellcodeverwaltung-Plug-In geladen. Diese Funktion wird nicht erwartet zurück, bis er abgeschlossen ist. Allerdings kann es mehrere Male mit mehreren Listen von Dateien, alle gleichzeitig aufgerufen werden.  
  
 Die Verwendung der `dwFlags` Argument ist identisch mit der [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)