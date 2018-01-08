---
title: SccGetParentProjectPath Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8395d73a48d4c8501ba834b2168b5bcbc8019b8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath-Funktion
Diese Funktion bestimmt den Projektpfad übergeordnete Element eines angegebenen Projekts. Diese Funktion wird aufgerufen, wenn der Benutzer ein Visual Studio-Projekt zur quellcodeverwaltung hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich der NULL-Terminator).  
  
 lpProjPath  
 [in] Zeichenfolge, die Pfad des Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator) identifiziert.  
  
 lpAuxProjPath  
 [in, out] Zusätzlichen Zeichenfolge, die das Projekt (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator) identifiziert.  
  
 lpParentProjPath  
 [in, out] Die Ausgabezeichenfolge identifizieren den Pfad des übergeordneten Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Pfad des übergeordneten Projekts wurde erfolgreich abgerufen.|  
|SCC_E_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte nicht auf die Datenquellen-Steuerelement-Plug-in anmelden.|  
|SCC_E_UNKNOWNPROJECT|Projekt ist das Quellsteuerelement-Plug-in nicht bekannt.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_CONNECTIONFAILURE|Problem mit der Verbindung zu speichern.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt einen Erfolg oder Misserfolg Code zurück, und bei Erfolg, füllt die Variable `lpParentProjPath` mit der vollständige Pfad zum angegebenen Projekt.  
  
 Diese Funktion gibt die übergeordnete Projektpfad eines vorhandenen Projekts. Für das Stammprojekt gibt die Funktion den Projektpfad, der übergeben wurde (d. h. den gleichen Stamm Projektpfad). Beachten Sie, dass eine Projektpfad eine Zeichenfolge, die nur für die Datenquellen-Steuerelement-Plug-in von Bedeutung ist.  
  
 Die IDE wird vorbereitet, zum Übernehmen der Änderungen an der `lpUser` und `lpAuxProjPath` auch Parameter. Die IDE wird diese Zeichenfolgen beibehalten und übergeben sie die [SccOpenProject](../extensibility/sccopenproject-function.md) Wenn der Benutzer öffnet dieses Projekt in der Zukunft. Diese Zeichenfolgen bieten eine Möglichkeit daher für die quellcodeverwaltung-Plug-in nachverfolgen-Informationen, die es benötigt, ein Projekt zugeordnet werden soll.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), außer dass es den Benutzer ein Projekt auswählen, nicht angefordert werden. Es erstellt auch nie ein neues Projekt aber funktioniert nur mit einem vorhandenen Projekt.  
  
 Wenn `SccGetParentProjectPath` aufgerufen wird, `lpProjPath` und `lpAuxProjPath` nicht leer sein und wird zu einem gültigen Projekt entsprechen. Diese Zeichenfolgen werden in der Regel von der IDE aus einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion.  
  
 Die `lpUser` Argument ist der Benutzername. Die IDE in den gleichen Benutzernamen, die zuvor vom empfangenen hatte übergibt die `SccGetProjPath` -Funktion und die Datenquellen-Steuerelement-Plug-in verwenden, sollten den Namen als den Standardwert. Wenn der Benutzer bereits eine offene Verbindung mit dem plug-in verfügt, sollte das plug-in versuchen, beseitigen alle Anweisungen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Jedoch, wenn die Anmeldung ein Fehler auftritt, das plug-in sollte den Benutzer auffordern für eine Anmeldung und beim Empfang einer gültigen Anmeldenamen, übergeben Sie der Namen wieder in `lpUser`. Da die-Plug-in dieser Zeichenfolge ändern kann, wird die IDE immer einen Puffer mit einer Größe zuweisen (`SCC_USER_LEN`+ 1). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die (zumindest als gültig mit der alten Zeichenfolge).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekte zur quellcodeverwaltung wurde in Visual Studio für die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte in das Quellcodeverwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in sowohl die neuen Funktionen unterstützt der [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) und die `SccGetParentProjectPath` Funktion. Allerdings kann die folgenden Registrierungseintrag verwendet werden, deaktivieren diese Änderungen, und klicken Sie auf das vorherige Verhalten von Visual Studio (Source Control-Plug-in-API-Version 1.1) zurücksetzen:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Wenn dieses Registrierungseintrags nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen zu verwenden `SccCreateSubProject`und`SccGetParentProjectPath`.  
  
 Wenn Sie der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, diese neuen Funktionen zu verwenden und die Vorgänge des Hinzufügens zur quellcodeverwaltung funktionieren, wie in früheren Versionen von Visual Studio.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)