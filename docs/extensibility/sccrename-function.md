---
title: SccRename Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c24d84ff659d287f3b32be2b5585ded16b148395
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccrename-function"></a>SccRename-Funktion
Diese Funktion benennt eine Datei in das Quellcodeverwaltungssystem.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 [in] Der vollqualifizierte Dateiname der Datei, die umbenannt wird.  
  
 lpNewName  
 [in] Der vollqualifizierte Name für neuen. Wenn der Pfad des Verzeichnisses unterscheidet, wurde die Datei aus einem Unterverzeichnis auf einen anderen verschoben.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Umbenennungsvorgang erfolgreich abgeschlossen.|  
|SCC_E_PROJNOTOPEN|Das Projekt kann nicht in der quellcodeverwaltung öffnen.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang abzuschließen.|  
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil der Umbenennungsvorgang erstellt werden.|  
|SCC_E_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|  
|SCC_E_NONSPECIFICERROR|Ein Unbekannter oder allgemeiner Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann verwendet werden, um eine Datei umbenennen oder verschieben es von einem Speicherort zu einem anderen, in das Quellcodeverwaltungssystem. Die Datenquellen-Steuerelements, das plug-in sollten nicht versuchen, auf die Datei auf dem Datenträger zuzugreifen. Es liegt in der IDE Verantwortung umbenennen die lokale Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)