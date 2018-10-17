---
title: SccRename-Funktion | Microsoft-Dokumentation
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
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ef59da920e8011e5b2a23e14dcd58cdc07365d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232207"
---
# <a name="sccrename-function"></a>SccRename-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion benennt eine Datei in das Quellcodeverwaltungssystem.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpFileName  
 [in] Der vollqualifizierte Dateiname der Datei, die umbenannt wird.  
  
 lpNewName  
 [in] Der vollqualifizierte neue Name. Wenn der Verzeichnispfad abweicht, wurde die Datei aus einem Unterverzeichnis auf einen anderen verschoben.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Umbenennungsvorgang wurde erfolgreich abgeschlossen.|  
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht in der quellcodeverwaltung öffnen.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang abzuschließen.|  
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil der Umbenennung erstellt werden.|  
|SCC_E_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|  
|SCC_E_NONSPECIFICERROR|Ein Unbekannter oder allgemeiner Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann zum Umbenennen einer Datei, oder es von einem Speicherort in einen anderen verschieben, in das Quellcodeverwaltungssystem verwendet werden. Das Quellcodeverwaltungs-Plug-Ins sollten nicht versuchen, Zugriff auf die Datei auf dem Datenträger. Es obliegt der IDE auf die lokale Datei umbenennen.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

