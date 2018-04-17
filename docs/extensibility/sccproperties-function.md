---
title: SccProperties Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d126a4691332f1121ebfc99a84b180d1e99f3d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
Diese Funktion zeigt die Quelle von Steuerelementeigenschaften für eine Datei oder das Projekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 [in] Der vollqualifizierte Pfadname der Datei oder des Projekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Eigenschaften wurden erfolgreich angezeigt.|  
|SCC_I_RELOADFILE|Versionskontrollsystems wurde die Dateieigenschaften geändert, damit die IDE diese Datei neu geladen werden soll.|  
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde nicht in der quellcodeverwaltung geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um Eigenschaften dieser Datei oder eines Projekts anzuzeigen.|  
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das Projekt ist nicht in der quellcodeverwaltung.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unbekannter oder allgemeine Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Die Datenquellen-Steuerelement-Plug-in zeigt die Eigenschaften in ein eigenes Dialogfeld.  
  
 Die Eigenschaften werden durch die quellcodeverwaltung-Plug-in definiert und unterscheidet sich möglicherweise von Plug-in-Plug-in. Wenn das plug-in die Benutzer zum Ändern der Eigenschaften des Datenquellen-Steuerelement einer Datei ermöglicht, sollte er zurück `SCC_I_RELOAD` die IDE zu signalisieren, die diese Datei oder das Projekt erneut geladen werden muss.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)