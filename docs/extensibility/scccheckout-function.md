---
title: SccCheckout Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 671e4ecebb44f0910eba3bb835a6da6f9a7f3903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137748"
---
# <a name="scccheckout-function"></a>SccCheckout-Funktion
Wenn Sie eine Liste der vollqualifizierten Dateinamen, checkt diese Funktion sie auf dem lokalen Laufwerk. Der Kommentar gilt für alle Dateien ausgecheckt wird. Das Kommentar-Argument kann eine `null` Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Anzahl der Dateien ausgecheckt werden ausgewählt.  
  
 lpFileNames  
 [in] Array der Namen von voll gekennzeichneter lokaler Pfad der Dateien ausgecheckt werden.  
  
 lpComment  
 [in] Kommentar auf einzelnen ausgewählten Dateien ausgecheckt wird, angewendet werden soll.  
  
 fOptions  
 [in] Befehl Flags (finden Sie unter [Bitflags verwendet wird, indem Sie bestimmte Befehle](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Auschecken war erfolgreich.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers. Die Datei wurde nicht ausgecheckt.|  
|SCC_E_ALREADYCHECKEDOUT|Der Benutzer hat bereits die Datei ausgecheckt.|  
|SCC_E_FILEISLOCKED|Die Datei ist gesperrt und zur Erstellung neuer Versionen.|  
|SCC_E_FILEOUTEXCLUSIVE|Ein anderer Benutzer hat exklusiv ausgecheckt für diese Datei ausgeführt werden.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)