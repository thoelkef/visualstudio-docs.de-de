---
title: SccCreateSubProject-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2f28d8bb9ebc440db69085324becb6a96c19afe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946194"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten-Projekt, das gemäß der `lpParentProjPath` Argument.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpParentProjPath  
 [in] Eine Zeichenfolge, die den Pfad des übergeordneten Projekts (maximal SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens) identifiziert.  
  
 lpSubProjName  
 [in] Der Name der vorgeschlagenen Unterprojekt (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpAuxProjPath  
 [in, out] Zusätzliche Zeichenfolge, die bestimmen, zu des Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpSubProjPath  
 [in, out] Die Ausgabezeichenfolge identifizieren den Pfad für das Teilprojekt (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Unterprojekt wurde erfolgreich erstellt.|  
|SCC_E_INITIALIZEFAILED|Übergeordnetes Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte nicht vom Quellcodeverwaltungssystem Anmeldung.|  
|SCC_E_COULDNOTCREATEPROJECT|Unterprojekt kann nicht erstellt werden.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_UNKNOWNPROJECT|Das übergeordnete Projekt ist das Quellcodeverwaltungs-Plug-in nicht bekannt.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_CONNECTIONFAILURE|Es wurde ein Verbindungsproblem Source Control-Plug-in.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Unterprojekt mit dem Namen bereits vorhanden ist, kann die Funktion den Standardnamen in einen eindeutigen, beispielsweise durch Hinzufügen von erstellen ändern "_\<Anzahl >" zuzuweisen. Der Aufrufer muss darauf vorbereitet sein, Änderungen zu übernehmen `lpUser`, `lpSubProjPath`, und `lpAuxProjPath`. Die `lpSubProjPath` und`lpAuxProjPath` Argumente werden in einem Aufruf verwendet die [SccOpenProject](../extensibility/sccopenproject-function.md). Sie sollten nicht von der aufrufenden Funktion bei der Rückgabe geändert werden. Diese Zeichenfolgen bieten eine Möglichkeit für das Quellcodeverwaltungs-Plug-in, um Informationen zu verfolgen, die mit einem-Projekt zuordnen muss. Diese beiden Parameter bei der Rückgabe wird von der Aufrufer IDE nicht angezeigt werden, da das plug-in eine formatierte Zeichenfolge verwenden können, die möglicherweise nicht geeignet für die Anzeige. Gibt die Funktion einen Erfolg oder Misserfolg Code und, wenn erfolgreich, füllt die Variable `lpSubProjPath` mit den vollständigen Projektpfad in das neue Projekt.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), außer dass der Benutzer aufgefordert, eine auswählen, anstatt ein Projekt im Hintergrund erstellt. Wenn die `SccCreateSubProject` Funktion wird aufgerufen, `lpParentProjName` und `lpAuxProjPath` ist nicht leer sein und ein gültiges Projekt entspricht. Diese Zeichenfolgen werden in der Regel von der IDE von einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion oder die [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Die `lpUser` Argument ist der Benutzername. Den gleichen Benutzernamen, die sie zuvor erhalten hat, aus die IDE übergibt `SccGetProjPath`, und das Quellcodeverwaltungs-Plug-in sollte den Namen als den Standardwert verwenden. Wenn der Benutzer bereits eine offene Verbindung mit dem plug-in verfügt, klicken Sie dann sollten das plug-in beseitigen alle aufforderungen, um sicherzustellen, dass die Funktion im Hintergrund arbeitet. Jedoch, wenn die Anmeldung ein Fehler auftritt, das plug-in sollte den Benutzer auffordern für eine Anmeldung und, wenn sie einen gültigen Anmeldenamen, übergeben Sie der Namen wieder empfängt `lpUser`. Da das plug-in dieser Zeichenfolge ändern können, die IDE wird immer ein Puffer der Größe (SCC_USER_LEN + 1 oder SCC_USER_SIZE, die Speicherplatz für das Nullabschlusszeichen enthält). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die (zumindest als gültig wie die alte Zeichenfolge) sein.  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekte zur quellcodeverwaltung wurde in Visual Studio, um die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte in das Quellcodeverwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in der neuen Funktionen, unterstützt `SccCreateSubProject` und `SccGetParentProjectPath`. Allerdings kann der folgenden Registrierungseintrag verwendet werden, deaktivieren diese Änderungen und revert zum früheren Verhalten von Visual Studio (Source Control-Plug-in-API-Version 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Wenn dieses Registrierungseintrags nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio verwenden Sie für die neuen Funktionen `SccCreateSubProject` und `SccGetParentProjectPath`.  
  
 Wenn der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, verwenden Sie diese neuen Funktionen und die Vorgänge des Hinzufügens zur quellcodeverwaltung arbeiten, wie in früheren Versionen von Visual Studio.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
