---
title: Sccquerychanges-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: baa6059a1668be5507994921cb96ac3ed1cfd5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200011"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion Listet eine angegebene Liste von Dateien auf, die Informationen über Namensänderungen für jede Datei über eine Rückruffunktion bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pContext  
 in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.  
  
 nnoch  
 in Anzahl der Dateien im `lpFileNames` Array.  
  
 lpfile-Namen  
 in Array von Dateinamen, über die Informationen erhalten werden.  
  
 pfncallback  
 in Rückruffunktion, die für jeden Dateinamen in der Liste aufgerufen werden soll (Weitere Informationen finden Sie unter [querychangesfunc](../extensibility/querychangesfunc.md) ).  
  
 pvcallerdata  
 in Der Wert, der unverändert an die Rückruffunktion übermittelt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Abfrageprozess wurde erfolgreich abgeschlossen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht in der Quell Code Verwaltung geöffnet.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen.|  
|SCC_E_NONSPECIFICERROR|Ein nicht spezifizierter oder allgemeiner Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Bemerkungen  
 Änderungen, die abgefragt werden, sind der Namespace: das Umbenennen, hinzufügen und Entfernen einer Datei.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Querychangesfunc](../extensibility/querychangesfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)
