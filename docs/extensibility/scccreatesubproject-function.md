---
title: SccCreateSubProject Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce9c4ec33a76afbba1b334fdc5bac5aee17e334
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject-Funktion
Diese Funktion wird ein Unterprojekt erstellt, mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt gemäß der `lpParentProjPath` Argument.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich der NULL-Terminator).  
  
 lpParentProjPath  
 [in] Eine Zeichenfolge, die den Pfad des übergeordneten Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator) identifiziert.  
  
 lpSubProjName  
 [in] Der Name der vorgeschlagenen Unterprojekt (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator).  
  
 lpAuxProjPath  
 [in, out] Zusätzlichen Zeichenfolge, die das Projekt (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator) identifiziert.  
  
 lpSubProjPath  
 [in, out] Die Ausgabezeichenfolge identifizieren den Pfad für das Teilprojekt (bis zu SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Unterprojekt wurde erfolgreich erstellt.|  
|SCC_E_INITIALIZEFAILED|Übergeordnetes Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte nicht vom Quellcodeverwaltungssystem anmelden.|  
|SCC_E_COULDNOTCREATEPROJECT|Unterprojekt kann nicht erstellt werden.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_UNKNOWNPROJECT|Übergeordnetes Projekt ist unbekannt, die Datenquellen-Steuerelement-Plug-in.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_CONNECTIONFAILURE|Es wurde ein Verbindungsproblem Source Control-Plug-in.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Unterprojekt mit dem Namen bereits vorhanden ist, kann die Funktion ändern den Standardnamen in einen eindeutigen Index, z. B. durch Hinzufügen von zu erstellen "_\<Anzahl >" darauf. Der Aufrufer muss darauf vorbereitet sein, Änderungen zu übernehmen `lpUser`, `lpSubProjPath`, und `lpAuxProjPath`. Die `lpSubProjPath` und`lpAuxProjPath` Argumente werden dann verwendet, in einem Aufruf der [SccOpenProject](../extensibility/sccopenproject-function.md). Sie sollten nicht von der aufrufenden Funktion bei der Rückgabe geändert werden. Diese Zeichenfolgen bieten eine Möglichkeit für die Datenquellen-Steuerelements, das plug-in, das Informationen zu verfolgen, die es einem zuordnen muss. Diese beiden Parameter nach der Rückgabe wird von der Aufrufer IDE nicht angezeigt werden, da das plug-in eine formatierte Zeichenfolge verwenden können, die möglicherweise nicht geeignet für die Anzeige. Die Funktion gibt einen Erfolg oder Misserfolg Code zurück, und bei Erfolg, füllt die Variable `lpSubProjPath` mit der vollständigen Pfad in das neue Projekt.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), außer dass der Benutzer aufgefordert, eine auswählen, anstatt ein Projekt im Hintergrund erstellt. Wenn die `SccCreateSubProject` Funktion wird aufgerufen, `lpParentProjName` und `lpAuxProjPath` nicht leer sein und wird zu einem gültigen Projekt entsprechen. Diese Zeichenfolgen werden in der Regel von der IDE aus einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion oder die [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Die `lpUser` Argument ist der Benutzername. Die IDE in den gleichen Benutzernamen, die zuvor vom empfangenen hatte übergibt `SccGetProjPath`, und die Datenquellen-Steuerelement-Plug-in sollte den Namen als den Standardwert verwenden. Wenn der Benutzer bereits eine offene Verbindung mit dem plug-in verfügt, sollte das plug-in versuchen, beseitigen alle Anweisungen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Jedoch, wenn die Anmeldung ein Fehler auftritt, das plug-in sollte den Benutzer auffordern für eine Anmeldung und beim Empfang einer gültigen Anmeldenamen, übergeben Sie der Namen wieder in `lpUser`. Da die-Plug-in dieser Zeichenfolge ändern kann, die IDE wird immer ein Puffer der Größe (SCC_USER_LEN + 1 oder SCC_USER_SIZE, die Speicherplatz für das Nullabschlusszeichen enthält). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die (zumindest als gültig mit der alten Zeichenfolge).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekte zur quellcodeverwaltung wurde in Visual Studio für die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte in das Quellcodeverwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in sowohl die neuen Funktionen unterstützt `SccCreateSubProject` und `SccGetParentProjectPath`. Die folgenden Registrierungseintrag kann jedoch verwendet werden, deaktivieren diese Änderungen und zum früheren Verhalten von Visual Studio (Source Control-Plug-in-API-Version 1.1) zurücksetzen:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Wenn dieses Registrierungseintrags nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen zu verwenden `SccCreateSubProject` und `SccGetParentProjectPath`.  
  
 Wenn Sie der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, diese neuen Funktionen zu verwenden und die Vorgänge des Hinzufügens zur quellcodeverwaltung funktionieren, wie in früheren Versionen von Visual Studio.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)