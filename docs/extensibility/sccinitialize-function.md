---
title: "SccInitialize-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize-Funktion"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccInitialize-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion initialisiert das Quellcodeverwaltungs\-Plug\-in sowie Funktionen und Grenzwerte auf der integrated Development Environment \(IDE\).  
  
## Syntax  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### Parameter  
 `ppvContext`  
 \[in\] Das Quellcodeverwaltungs\-Plug\-in kann einen Zeiger auf die Kontextstruktur hier platzieren.  
  
 `hWnd`  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 `lpCallerName`  
 \[in\] Der Name des aufrufenden das Quellcodeverwaltungs\-Plug\-in.  
  
 `lpSccName`  
 \[in, out\] Der Puffer, in dem das Quellcodeverwaltungs\-Plug\-in einen eigenen Namen setzt \(nicht `SCC_NAME_LEN`\).  
  
 `lpSccCaps`  
 \[out\] Gibt das Quellcodeverwaltungs\-Plug\-ins Fähigkeitskennzeichen zurück.  
  
 `lpAuxPathLabel`  
 \[in, out\] Der Puffer, in dem das Quellcodeverwaltungs\-Plug\-in setzt eine Zeichenfolge, die beschreibt, die `lpAuxProjPath` Parameter zurückgegebene die [SccOpenProject](../extensibility/sccopenproject-function.md) und die [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(nicht `SCC_AUXLABEL_LEN`\).  
  
 `pnCheckoutCommentLen`  
 \[out\] Gibt die maximale zulässige Länge für einen Kommentar zurück.  
  
 `pnCommentLen`  
 \[out\] Gibt die maximale zulässige Länge für andere Kommentare.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Initialisierung des Datenquellen\-Steuerelements war erfolgreich.|  
|SCC\_E\_INITIALIZEFAILED|System konnte nicht initialisiert werden.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist für den angegebenen Vorgang nicht zulässig.|  
|SCC\_E\_NONSPECFICERROR|Unspezifischen Ausfall. Quellcode\-Verwaltungssystem wurde nicht initialisiert.|  
  
## Hinweise  
 Die IDE ruft diese Funktion beim ersten der Datenquellen\-Steuerelement\-Plug\-In laden. Sie können die IDE, um bestimmte Informationen, z. B. den Namen des Aufrufers an, um das plug\-in übergeben. Die IDE erhalten auch bestimmte Informationen wie z. B. die maximal zulässige Länge für Kommentare und das Plug\-in Funktionen.  
  
 Die `ppvContext` verweist auf eine `NULL` Zeiger. Das Quellcodeverwaltungs\-Plug\-in eine Struktur zur eigenen Verwendung zuordnen kann, und speichern Sie einen Zeiger auf diese Struktur in `ppvContext`. Die IDE übergibt this\-Zeiger an jede andere VSSCI\-API\-Funktion ermöglicht das plug\-in Kontextinformationen zur Verfügung zu haben, ohne zu globalen Speicher und Unterstützung für mehrere Instanzen des Plug\-Ins. Diese Struktur sollte freigegeben werden, wenn die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Die `lpCallerName` und `lpSccName` Parameter ermöglichen die IDE und das Datenquellen\-Steuerelement, das Plug\-in\-Namen austauschen. Diese Namen können werden lediglich verwendet, um mehrere Instanzen unterscheiden zu können, oder sie möglicherweise tatsächlich in Menüs oder Dialogfeldern angezeigt.  
  
 Die `lpAuxPathLabel` Parameter ist eine Zeichenfolge, die als Kommentar verwendet werden, um zusätzliche Projektpfad zu identifizieren, die in der Projektmappendatei gespeichert wird, und das Datenquellen\-Steuerelement\-Plug\-in in einem Aufruf an die [SccOpenProject](../extensibility/sccopenproject-function.md).[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] die Zeichenfolge "SourceSafe\-Projekt:"; andere Datenquellen\-Steuerelement\-Plug\-ins sollte nicht zu dieser bestimmte Zeichenfolge verwenden.  
  
 Die `lpSccCaps` Parameter enthält das Datenquellen\-Steuerelement\-Plug\-in einen Ort zum Speichern von Bitflags, die die\-Plug\-ins Funktionen angibt. \(Eine vollständige Liste der Funktionen Bitflags, finden Sie unter [Capability Flags](../extensibility/capability-flags.md)\). Zum Beispiel wenn die Plug\-in\-Pläne, Ergebnisse in ein vom Aufrufer bereitgestellter Callback\-Funktion zu schreiben, das plug\-in wird die Funktion festgelegt SCC\_CAP\_TEXTOUT bit. Dies würde die IDE zum Erstellen eines Fensters für Version Control Ergebnisse zu signalisieren.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Capability Flags](../extensibility/capability-flags.md)