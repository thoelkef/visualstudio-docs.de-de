---
title: SccProperties-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb8fd8172468dc1fc4d60d0f5e36ee7b4f9a588
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511064"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccProperties-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccproperties-function).  
  
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

