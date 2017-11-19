---
title: SccQueryInfo Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryInfo
helpviewer_keywords: SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5c2e974fe2cd0f6d95b97bba0ba2ffa22c1095e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo-Funktion
Diese Funktion ruft die Statusinformationen für einen Satz von ausgewählten Dateien unter quellcodeverwaltung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 nFiles  
 [in] Anzahl der Dateien im angegebenen der `lpFileNames` Array und die Länge der `lpStatus` Array.  
  
 lpFileNames  
 [in] Ein Array von Namen der Dateien, die abgefragt werden.  
  
 lpStatus  
 [in, out] Ein Array, in dem das Quellsteuerelement-Plug-in die Statusflags für jede Datei zurückgegeben. Weitere Informationen finden Sie unter [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Abfrage war erfolgreich.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem mit den Zugriff auf das Quellcodeverwaltungssystem wurde wahrscheinlich durch Netzwerk-oder Konflikte verursacht. Eine Wiederholung wird empfohlen.|  
|SCC_E_PROJNOTOPEN|Das Projekt kann nicht in der quellcodeverwaltung öffnen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `lpFileName` ist eine leere Zeichenfolge besteht zurzeit keine Statusinformationen zu aktualisieren. Andernfalls ist es der vollständige Pfadname der Datei für die die Statusinformationen geändert haben kann.  
  
 Die zurückgegebenen Array kann eine Bitmaske der `SCC_STATUS_xxxx` Bits. Weitere Informationen finden Sie unter [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md). Ein Quellcodeverwaltungssystem unterstützen möglicherweise nicht alle Bitdatentypen. Z. B. wenn `SCC_STATUS_OUTOFDATE` nicht angeboten wird, wird das Bit nicht festgelegt ist.  
  
 Wenn Sie diese Funktion beim Auschecken der Dateien verwenden, beachten Sie Folgendes `MSSCCI` Status Anforderungen:  
  
-   `SCC_STATUS_OUTBYUSER`wird festgelegt, wenn der aktuelle Benutzer die Datei ausgecheckt hat.  
  
-   `SCC_STATUS_CHECKEDOUT`kann nicht festgelegt werden, es sei denn, `SCC_STATUS_OUTBYUSER` festgelegt ist.  
  
-   `SCC_STATUS_CHECKEDOUT`Wenn die Datei in das angegebene Arbeitsverzeichnis ausgecheckt ist, wird nur festgelegt werden.  
  
-   Wenn die Datei vom aktuellen Benutzer in ein Verzeichnis als das Arbeitsverzeichnis ausgecheckt ist `SCC_STATUS_OUTBYUSER` festgelegt ist, aber `SCC_STATUS_CHECKEDOUT` nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md)