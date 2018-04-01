---
title: SccDirQueryInfo Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c7a930c0fcdffbc76bba431012d76dd6d13686d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo-Funktion
Diese Funktion überprüft eine Liste der vollständig qualifizierte Verzeichnisse für ihren aktuellen Status an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 nDirs  
 [in] Die Anzahl der Verzeichnisse, die abgefragt werden ausgewählt.  
  
 lpDirNames  
 [in] Ein Array von voll qualifizierten Pfade der Verzeichnisse abgefragt werden.  
  
 lpStatus  
 [in, out] Eine Arraystruktur für die Datenquellen-Steuerelement-Plug-in die Statusflags zurückgeben (finden Sie unter [Statuscode "Directory"](../extensibility/directory-status-code-enumerator.md) Einzelheiten).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Abfrage war erfolgreich.|  
|SCC_E_OPNOTSUPPORTED|Dieser Vorgang wird von der Quellcodeverwaltungs-System nicht unterstützt.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion füllt das return Array mit einer Bitmaske der Bits aus der `SCC_DIRSTATUS` Familie (finden Sie unter [Statuscode "Directory"](../extensibility/directory-status-code-enumerator.md)), einen Eintrag für jedes Verzeichnis angegeben. Der Statusarray, die vom Aufrufer zugeordnet ist.  
  
 Die IDE verwendet diese Funktion auf, bevor ein Verzeichnis umbenannt wird, um zu überprüfen, ob das Verzeichnis in der quellcodeverwaltung ist von Abfragen, ob es sich um eine entsprechende Projekt verfügt. Wenn das Verzeichnis nicht in der quellcodeverwaltung ist, kann die IDE die richtige Warnung für dem Benutzer bereitstellen.  
  
> [!NOTE]
>  Wenn ein Quellcodeverwaltungs-Plug-in entscheidet, eine oder mehrere der Statuswerte nicht implementieren, sollten nicht implementierte Bits auf NULL festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Statuscode "Directory"](../extensibility/directory-status-code-enumerator.md)