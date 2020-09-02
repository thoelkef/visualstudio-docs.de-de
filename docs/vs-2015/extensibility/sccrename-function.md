---
title: Sccrename-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e78975acab0bf30f1f188cdd7b6454fd6e74ce6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143720"
---
# <a name="sccrename-function"></a>SccRename-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion benennt eine Datei in das Quell Code Verwaltungssystem um.  
  
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
 pvcontext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 lpFileName  
 in Der voll qualifizierte Dateiname der Datei, die umbenannt wird.  
  
 lpnewname  
 [in] Der vollqualifizierte neue Name. Wenn der Verzeichnispfad anders ist, wird die Datei von einem Unterverzeichnis in ein anderes verschoben.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Umbenennungs Vorgang wurde erfolgreich abgeschlossen.|  
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht unter Quell Code Verwaltung geöffnet.|  
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, diesen Vorgang abzuschließen.|  
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil des Umbenennungs Prozesses erstellt werden.|  
|SCC_E_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|  
|SCC_E_NONSPECIFICERROR|Ein nicht spezifizierter oder allgemeiner Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion kann verwendet werden, um eine Datei umzubenennen oder im Quell Code Verwaltungssystem von einem Speicherort zu einem anderen zu verschieben. Das Quellcodeverwaltungs-Plug-in sollte nicht versuchen, auf die Datei auf dem Datenträger zuzugreifen. Es liegt in der Verantwortung der IDE, die lokale Datei umzubenennen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
