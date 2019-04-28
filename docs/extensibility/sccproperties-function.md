---
title: SccProperties-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 519a17e7596a9cea479eeb24799724919d49bd45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433044"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion zeigt die Eigenschaften für eine Datei oder das Projekt der quellcodeverwaltung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpFileName  
 [in] Der Name der vollqualifizierte Pfad der Datei oder des Projekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Eigenschaften wurden erfolgreich angezeigt.|  
|SCC_I_RELOADFILE|Das Versionskontrollsystem wurde die Dateieigenschaften geändert, damit die IDE die Datei neu geladen werden soll.|  
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde nicht in der quellcodeverwaltung geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um die Eigenschaften dieser Datei oder eines Projekts anzuzeigen.|  
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das Projekt ist nicht unter quellcodeverwaltung.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unbekannter oder allgemeine Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Das Quellcodeverwaltungs-Plug-in zeigt die Eigenschaften in ein eigenes Dialogfeld.  
  
 Die Eigenschaften werden durch das Quellcodeverwaltungs-Plug-in definiert und können unterscheidet sich vom aus-Plug-in-Plug-in. Wenn das plug-in des Benutzers zum Ändern der Eigenschaften einer Datei der quellcodeverwaltung zulässt, sollte es zurückgeben `SCC_I_RELOAD` um der IDE zu signalisieren, die diese Datei oder das Projekt neu geladen werden muss.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
