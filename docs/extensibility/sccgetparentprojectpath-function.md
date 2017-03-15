---
title: "SccGetParentProjectPath-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath-Funktion"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccGetParentProjectPath-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion bestimmt den übergeordnete Pfad eines angegebenen Projekts. Diese Funktion wird aufgerufen, wenn der Benutzer Datenquellen\-Steuerelement eine Visual Studio\-Projekt hinzugefügt wird.  
  
## Syntax  
  
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
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 \[in, out\] Der Benutzername \(bis zu SCC\_USER\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpProjPath  
 \[in\] Zeichenfolge, die den Projektpfad \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpAuxProjPath  
 \[in, out\] Zusätzliche Zeichenfolge identifizieren das Projekt \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpParentProjPath  
 \[in, out\] Die Ausgabezeichenfolge Identifizieren des übergeordnete Pfads \(bis zu SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Pfad des übergeordneten Projekts wurde erfolgreich abgerufen.|  
|SCC\_E\_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC\_E\_INVALIDUSER|Der Benutzer konnte nicht auf das Quellcodeverwaltungs\-Plug\-in anmelden.|  
|SCC\_E\_UNKNOWNPROJECT|Projekt ist das Quellcodeverwaltungs\-Plug\-in nicht bekannt.|  
|SCC\_E\_INVALIDFILEPATH|Ungültige oder nicht mehr Dateipfad.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC\_E\_CONNECTIONFAILURE|Verbindungsproblem zu speichern.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Diese Funktion gibt einen Erfolg oder Fehler\-Code zurück, und bei Erfolg wird die Variable `lpParentProjPath` mit der vollständige Pfad zum angegebenen Projekt.  
  
 Diese Funktion gibt das übergeordnete Element Projektpfad eines vorhandenen Projekts. Für das Stammprojekt, gibt die Funktion den Pfad, der übergeben wurde \(d. h. die gleiche Projekt Stammpfad\). Beachten Sie, dass eine Projektpfad eine Zeichenfolge, die nur für das Quellcodeverwaltungs\-Plug\-in von Bedeutung ist.  
  
 Die IDE wird vorbereitet, um die Änderungen zu übernehmen die `lpUser` und `lpAuxProjPath` sowie Parameter. Die IDE wird diese Zeichenfolgen beibehalten und übergeben sie die [SccOpenProject](../extensibility/sccopenproject-function.md) Wenn der Benutzer öffnet dieses Projekt in der Zukunft. Diese Zeichenfolgen können daher für das Quellcodeverwaltungs\-Plug\-in Trackinformationen, die einem zugeordnet werden muss.  
  
 Diese Funktion ist vergleichbar mit der [SccGetProjPath](../extensibility/sccgetprojpath-function.md), außer dass es fordert nicht den Benutzer ein Projekt auswählen. Es erstellt auch nie ein neues Projekt, sondern nur mit einem vorhandenen Projekt.  
  
 Wenn `SccGetParentProjectPath` aufgerufen wird, `lpProjPath` und `lpAuxProjPath` nicht leer sein und ein gültiges Projekt entspricht. Diese Zeichenfolgen werden in der Regel von der IDE aus einem vorherigen Aufruf empfangen die `SccGetProjPath` Funktion.  
  
 Die `lpUser` Argument ist der Benutzername. Die IDE übergibt den gleichen Benutzernamen, die Sie zuvor aus erhalten hatte die `SccGetProjPath` \-Funktion, und das Quellcodeverwaltungs\-Plug\-in sollte der Name als Standardwert verwendet. Verfügt der Benutzer bereits eine offene Verbindung mit dem plug\-in, versuchen das plug\-in, zu beseitigen alle Anweisungen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Allerdings schlägt die Anmeldung das plug\-in sollte den Benutzer auffordern für eine Anmeldung und erhält eine gültige Anmeldung, übergeben Sie der Namen wieder `lpUser`. Da das plug\-in diese Zeichenfolge geändert werden kann, die IDE immer einen Puffer der Größe zuzuordnen \(`SCC_USER_LEN`\+ 1\). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename, die \(zumindest als gültig wie die alte Zeichenfolge\) sein.  
  
## Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath  
 Hinzufügen von Projektmappen und Projekten zur quellcodeverwaltung wurde in Visual Studio, um die Anzahl der zu minimieren, die ein Benutzer aufgefordert wird, wählen Sie Speicherorte im Quellcode\-Verwaltungssystem vereinfacht. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs\-Plug\-in sowohl die neuen Funktionen unterstützt, die [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) und die `SccGetParentProjectPath` Funktion. Der folgenden Registrierungseintrag kann jedoch verwendet werden, deaktivieren diese Änderungen und das vorherige Verhalten von Visual Studio \(Source Control\-Plug\-in API\-Version 1.1\) zurücksetzen:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= DWORD: 00000001  
  
 Wenn dieser Registrierungseintrag nicht vorhanden oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, verwenden Sie die neuen Funktionen, `SccCreateSubProject`und`SccGetParentProjectPath`.  
  
 Wenn der Registrierungseintrag auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, diese neuen Funktionen zu verwenden und die Vorgänge zur Versionskontrolle hinzufügen arbeiten, wie in früheren Versionen von Visual Studio.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)