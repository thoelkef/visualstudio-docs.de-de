---
title: SccQueryChanges Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryChanges
helpviewer_keywords: SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 589013b996f9ed018e28292a27c6a760eef1dae7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccquerychanges-function"></a>SccQueryChanges-Funktion
Diese Funktion Listet eine angegebene Liste mit Dateien, die Angabe von Informationen zu Änderungen des Computernamens für jede Datei über eine Rückruffunktion an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 nFiles  
 [in] Anzahl der Dateien im `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array von Dateinamen, zu dem Informationen abgerufen.  
  
 pfnCallback  
 [in] Rückruffunktion für jedes Dateinamen in der Liste aufrufen (siehe [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Einzelheiten).  
  
 pvCallerData  
 [in] Wert, der unverändert an die Rückruffunktion übergeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Abfrageprozess erfolgreich abgeschlossen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht in der quellcodeverwaltung geöffnet.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte.|  
|SCC_E_NONSPECIFICERROR|Ein Unbekannter oder allgemeiner Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Änderungen, die abgefragt wird, die auf den Namespace sind: insbesondere umbenennen, hinzufügen und Entfernen einer Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)