---
title: "SccCreateSubProject-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject-Funktion"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# SccCreateSubProject-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt anhand der `lpParentProjPath` Argument.  
  
## Syntax  
  
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
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 \[in, out\] Der Benutzername \(bis zu SCC\_USER\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpParentProjPath  
 \[in\] Eine Zeichenfolge, die den Pfad des übergeordneten Projekts \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\) identifiziert.  
  
 lpSubProjName  
 \[in\] Der Name der vorgeschlagenen Unterprojekt \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpAuxProjPath  
 \[in, out\] Zusätzliche Zeichenfolge identifizieren das Projekt \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpSubProjPath  
 \[in, out\] Die Ausgabezeichenfolge identifizieren den Pfad für das Teilprojekt \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Unterprojekt wurde erfolgreich erstellt.|  
|SCC\_E\_INITIALIZEFAILED|Übergeordnetes Projekt konnte nicht initialisiert werden.|  
|SCC\_E\_INVALIDUSER|Der Benutzer konnte nicht in das Quellcodeverwaltungssystem anmelden.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Unterprojekt kann nicht erstellt werden.|  
|SCC\_E\_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC\_E\_UNKNOWNPROJECT|Das übergeordnete Projekt ist das Quellcodeverwaltungs\-Plug\-in nicht bekannt.|  
|SCC\_E\_INVALIDFILEPATH|Ungültige oder nicht mehr Dateipfad.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_CONNECTIONFAILURE|Es wurde ein Verbindungsproblem Source Control\-Plug\-in.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Wenn ein Unterprojekt mit dem Namen bereits vorhanden ist, kann die Funktion den Standardnamen in erstellen eine eindeutige beispielsweise durch Hinzufügen von "\_ \< Anzahl \>" zu ändern. Der Aufrufer muss darauf vorbereitet sein, um Änderungen zu übernehmen, `lpUser`, `lpSubProjPath`, und `lpAuxProjPath`. Die `lpSubProjPath` und`lpAuxProjPath` Argumente werden dann in einem Aufruf verwendet den [SccOpenProject](../extensibility/sccopenproject-function.md). Sie dürfen nicht vom Aufrufer bei der Rückgabe geändert werden. Diese Zeichenfolgen bieten eine Möglichkeit für das Quellcodeverwaltungs\-Plug\-in, um Informationen nachzuverfolgen, die einem Projekt zugeordnet werden muss. Der Aufrufer IDE werden diese beiden Parameter bei der Rückgabe nicht angezeigt, da das plug\-in eine formatierte Zeichenfolge verwenden können, die möglicherweise nicht geeignet für die Anzeige. Gibt die Funktion einen Erfolg oder Fehler Code und, falls erfolgreich, füllt die Variable `lpSubProjPath` mit der vollständigen Pfad in das neue Projekt.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), außer dass der Benutzer aufgefordert, eine auswählen, anstatt ein Projekt im Hintergrund erstellt. Wenn die `SccCreateSubProject` Funktion aufgerufen wird, `lpParentProjName` und `lpAuxProjPath` nicht leer sein und ein gültiges Projekt entspricht. Diese Zeichenfolgen werden in der Regel von der IDE aus einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion oder die [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Die `lpUser` Argument ist der Benutzername. Die IDE übergibt den gleichen Benutzernamen, die Sie zuvor aus erhalten hatte `SccGetProjPath`, und das Quellcodeverwaltungs\-Plug\-in sollte diesen Namen als den Standardwert verwenden. Verfügt der Benutzer bereits eine offene Verbindung mit dem plug\-in, versuchen das plug\-in, zu beseitigen alle Anweisungen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Allerdings schlägt die Anmeldung das plug\-in sollte den Benutzer auffordern für eine Anmeldung und erhält eine gültige Anmeldung, übergeben Sie der Namen wieder `lpUser`. Da das plug\-in dieser Zeichenfolge ändern können, die IDE wird immer ein Puffer der Größe \(SCC\_USER\_LEN \+ 1 oder SCC\_USER\_SIZE, der Speicherplatz für den null\-Terminator enthält\). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die \(zumindest als gültig wie die alte Zeichenfolge\) sein.  
  
## Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekten zur quellcodeverwaltung wurde in Visual Studio, um die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte im Quellcode\-Verwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs\-Plug\-in sowohl die neuen Funktionen unterstützt `SccCreateSubProject` und `SccGetParentProjectPath`. Der folgenden Registrierungseintrag kann jedoch verwendet werden, deaktivieren diese Änderungen und zum früheren Verhalten von Visual Studio \(Source Control\-Plug\-in API\-Version 1.1\) zurücksetzen:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= DWORD: 00000001  
  
 Wenn dieser Registrierungseintrag nicht vorhanden oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, verwenden Sie die neuen Funktionen, `SccCreateSubProject` und `SccGetParentProjectPath`.  
  
 Wenn der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, diese neuen Funktionen zu verwenden und die Vorgänge zur Versionskontrolle hinzufügen arbeiten, wie in früheren Versionen von Visual Studio.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)