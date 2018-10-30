---
title: SccGetParentProjectPath-Funktion | Microsoft-Dokumentation
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
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71ddff2167331936fedf16cecd3d7d4cd48b22b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902644"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion bestimmt den übergeordnete Pfad eines angegebenen Projekts. Diese Funktion wird aufgerufen, wenn der Benutzer ein Visual Studio-Projekt zur quellcodeverwaltung hinzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpProjPath  
 [in] Zeichenfolge, die den Projektpfad (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens) identifiziert.  
  
 lpAuxProjPath  
 [in, out] Zusätzliche Zeichenfolge, die bestimmen, zu des Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpParentProjPath  
 [in, out] Die Ausgabezeichenfolge identifizieren den Pfad des übergeordneten Projekts (maximal SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Pfad des übergeordneten Projekts wurde erfolgreich abgerufen.|  
|SCC_E_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht anmelden, auf das Quellcodeverwaltungs-Plug-in zu können.|  
|SCC_E_UNKNOWNPROJECT|Projekt ist das Quellcodeverwaltungs-Plug-in nicht bekannt.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_CONNECTIONFAILURE|Store-Verbindungsproblem.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt einen Code zum Erfolg oder Fehler zurück und, wenn erfolgreich, füllt die Variable `lpParentProjPath` mit der vollständige Pfad zum angegebenen Projekt.  
  
 Diese Funktion gibt das übergeordnete Projektpfad eines vorhandenen Projekts. Für das Root-Projekt, die Funktion gibt den Pfad des Projekts, der übergeben wurde (d. h. den gleichen Stamm Projektpfad). Beachten Sie, dass ein Pfad des Projekts eine Zeichenfolge, die nur für das Quellcodeverwaltungs-Plug-in von Bedeutung ist.  
  
 Die IDE wird vorbereitet, um das Übernehmen von Änderungen an der `lpUser` und `lpAuxProjPath` auch Parameter. Speichern Sie diese Zeichenfolgen und übergeben sie die IDE wird die [SccOpenProject](../extensibility/sccopenproject-function.md) Wenn der Benutzer öffnet dieses Projekt in der Zukunft. Diesen Zeichenfolgen bieten daher eine Möglichkeit für das Quellcodeverwaltungs-Plug-in verfolgen-Informationen, die es benötigt, ein Projekt zugeordnet werden soll.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), mit dem Unterschied, dass es keine den Benutzer um ein Projekt auszuwählen. Es erstellt auch nie ein neues Projekt, aber funktioniert nur mit einem vorhandenen Projekt.  
  
 Wenn `SccGetParentProjectPath` aufgerufen wird, `lpProjPath` und `lpAuxProjPath` ist nicht leer sein und ein gültiges Projekt entspricht. Diese Zeichenfolgen werden in der Regel von der IDE von einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion.  
  
 Die `lpUser` Argument ist der Benutzername. Den gleichen Benutzernamen, die sie zuvor erhalten hat, aus die IDE übergibt die `SccGetProjPath` -Funktion, und das Quellcodeverwaltungs-Plug-in sollte verwenden Sie den Namen als den Standardwert. Wenn der Benutzer bereits eine offene Verbindung mit dem plug-in verfügt, klicken Sie dann sollten das plug-in beseitigen alle aufforderungen, um sicherzustellen, dass die Funktion im Hintergrund arbeitet. Jedoch, wenn die Anmeldung ein Fehler auftritt, das plug-in sollte den Benutzer auffordern für eine Anmeldung und, wenn sie einen gültigen Anmeldenamen, übergeben Sie der Namen wieder empfängt `lpUser`. Da das plug-in dieser Zeichenfolge ändern kann, die IDE wird immer ein Puffer der Größe (`SCC_USER_LEN`+ 1). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die (zumindest als gültig wie die alte Zeichenfolge) sein.  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekte zur quellcodeverwaltung wurde in Visual Studio, um die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte in das Quellcodeverwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in der neuen Funktionen, unterstützt die [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) und `SccGetParentProjectPath` Funktion. Allerdings kann der folgenden Registrierungseintrag verwendet werden, um diese Änderungen deaktivieren, und klicken Sie auf das vorherige Verhalten von Visual Studio (Source Control-Plug-in-API-Version 1.1) zurückgesetzt:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Wenn dieses Registrierungseintrags nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio verwenden Sie für die neuen Funktionen `SccCreateSubProject`und`SccGetParentProjectPath`.  
  
 Wenn der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, verwenden Sie diese neuen Funktionen und die Vorgänge des Hinzufügens zur quellcodeverwaltung arbeiten, wie in früheren Versionen von Visual Studio.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

