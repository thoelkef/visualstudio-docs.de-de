---
title: "SccOpenProject-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject-Funktion"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccOpenProject-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion wird eine vorhandene Quellcodeverwaltungsprojekt geöffnet oder erstellt eine neue.  
  
## Syntax  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 \[in, out\] Der Name des Benutzers \(nicht zu überschreiten SCC\_USER\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpProjName  
 \[in\] Die Zeichenfolge, die den Namen des Projekts.  
  
 lpLocalProjPath  
 \[in\] Der Pfad zum Arbeitsordner für das Projekt.  
  
 lpAuxProjPath  
 \[in, out\] Eine optionale zusätzliche\-Zeichenfolge, die das Projekt \(nicht zu überschreiten SCC\_AUXPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\) identifiziert.  
  
 lpComment  
 \[in\] Kommentieren Sie in ein neues Projekt, das erstellt wird.  
  
 lpTextOutProc  
 \[in\] Eine optionale Rückruffunktion zum Anzeigen von Text aus dem Quellsteuerelement Plug\-in\-Ausgabe.  
  
 dwFlags  
 \[in\] Signale steuern, ob ein neues Projekt muss erstellt werden, wenn das Projekt in der Quelle unbekannt\-Plug\-in. Wert kann eine Kombination von `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN.`  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Erfolg in das Projekt geöffnet.|  
|SCC\_E\_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC\_E\_INVALIDUSER|Der Benutzer konnte nicht in das Quellcodeverwaltungssystem anmelden.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Das Projekt vor dem Aufruf nicht vorhanden.  die `SCC_OPT_CREATEIFNEW` \-Flag festgelegt wurde, aber das Projekt konnte nicht erstellt werden.|  
|SCC\_E\_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC\_E\_UNKNOWNPROJECT|Das Projekt ist unbekannt, das Quellcodeverwaltungs\-Plug\-in, und die `SCC_OPT_CREATEIFNEW` Flag nicht festgelegt wurde.|  
|SCC\_E\_INVALIDFILEPATH|Ungültige oder nicht mehr Dateipfad.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECFICERROR|Ein unspezifischen Fehler; Quellcode\-Verwaltungssystem wurde nicht initialisiert.|  
  
## Hinweise  
 Die IDE möglicherweise einen Benutzernamen übergeben \(`lpUser`\), oder es kann einfach übergeben Sie einen Zeiger auf eine leere Zeichenfolge. Wenn ein Benutzername vorhanden ist, sollten das Quellcodeverwaltungs\-Plug\-in als Standard verwenden. Allerdings, wenn kein Name übergeben wurde, oder wenn Fehler bei der Anmeldung mit dem angegebenen Namen, das plug\-in sollte den Benutzer aufzufordern, melden Sie sich und sieht den gültigen Name in `lpUser` empfängt eine gültige Anmeldung`.` da das plug\-in die Benutzernamen\-Zeichenfolge ändern kann, die IDE wird immer ein Puffer der Größe \(`SCC_USER_LEN`\+ 1 oder SCC\_USER\_SIZE, der Speicherplatz für den null\-Terminator enthält\).  
  
> [!NOTE]
>  Die erste Aktion die IDE kann zum Ausführen von möglicherweise ein Aufruf der `SccOpenProject` Funktion oder die [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Aus diesem Grund haben beide eine identische `lpUser` Parameter.  
  
 `lpAuxProjPath` und`lpProjName` werden von der Projektmappendatei, gelesen oder sie von einem Aufruf von zurückgegeben werden die `SccGetProjPath` Funktion. Diese Parameter enthalten die Zeichenfolgen, die das Quellcodeverwaltungs\-Plug\-in mit dem Projekt verknüpft und werden nur für das plug\-in von Bedeutung. Wenn keine solche Zeichenfolgen in die Projektmappendatei und der Benutzer nicht aufgefordert hat, zu wechseln \(würde die Zeichenfolge über Zurückgeben der `SccGetProjPath` Funktion\), die IDE übergibt leere Zeichenfolgen für beide `lpAuxProjPath` und `lpProjName`, und erwartet, dass diese Werte vom plug\-in aktualisiert werden, wenn diese Funktion zurückkehrt.  
  
 `lpTextOutProc` ist ein Zeiger auf eine Rückruffunktion, die von der IDE\-Plug\-In für die Anzeige der Ausgabe des Befehls Ergebnis von dem Datenquellen\-Steuerelement bereitgestellt. Diese Callback\-Funktion wird ausführlich beschrieben [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Will, dass das Quellcodeverwaltungs\-Plug\-in profitieren, es festgelegt haben die `SCC_CAP_TEXTOUT` \-flag in der [SccInitialize](../extensibility/sccinitialize-function.md). Wenn dieses Flag nicht festgelegt wurde oder wenn die IDE dieses Feature nicht unterstützt `lpTextOutProc` werden `NULL`.  
  
 Die `dwFlags` Parameter steuert das Ergebnis, wenn das Projekt geöffnet wird derzeit nicht vorhanden ist. Es besteht aus zwei Bitflags `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN`. Wenn das Projekt geöffnet wird, bereits vorhanden ist, die Funktion wird das Projekt geöffnet und gibt `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` Flag ist auf, das Quellcodeverwaltungs\-Plug\-in kann Erstellen des Projekts in das Quellcodeverwaltungssystem, öffnen Sie es, und `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` \-Flag ist deaktiviert, das plug\-in sollte überprüfen Sie, ob die `SCC_OP_SILENTOPEN` Flag. Wenn dieses Flag nicht aktiviert ist, kann das plug\-in der Benutzer einen Projektnamen aufgefordert. Wenn dieses Flag aktiviert ist, das plug\-in muss einfach zurückgeben `SCC_E_UNKNOWNPROJECT`.  
  
## Aufrufen der Reihenfolge  
 Während der normalen von Ereignissen die [SccInitialize](../extensibility/sccinitialize-function.md) würde zuerst aufgerufen werden, um eine Source Control\-Sitzung zu öffnen. Eine Sitzung bestehen aus einem Aufruf von `SccOpenProject`, gefolgt von den anderen Source Control\-Plug\-in API\-Funktionsaufrufe und endet mit einem Aufruf der [SccCloseProject](../extensibility/scccloseproject-function.md). Diese Sitzung können mehrmals vor wiederholt werden die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Wenn der Quellcode\-Plug\-in legt die `SCC_CAP_REENTRANT` bit im `SccInitialize`, und klicken Sie dann die oben angegebene Reihenfolge der Sitzung parallel mehrmals wiederholt werden kann. Verschiedene `pvContext` Strukturen nachverfolgen, die anderen Sitzungen, in denen die einzelnen `pvContext` gleichzeitig mit einem geöffneten Projekt verknüpft ist. Auf der Grundlage der`pvContext` \-Parameter des Plug\-Ins können bestimmen, welches Projekt in einem bestimmten Aufruf verwiesen wird. Wenn die Funktion bit `SCC_CAP_REENTRANT` nicht festgelegt ist, nonreentrant Source Control\-Plug\-ins sind in der Lage, arbeiten mit mehreren Projekten beschränkt.  
  
> [!NOTE]
>  Das `SCC_CAP_REENTRANT` Bit wurde in Version 1.1 der Source Control\-Plug\-in\-API eingeführt. Es ist nicht festgelegt oder ist in Version 1.0 ignoriert, und alle Version 1.0 Source Control\-Plug\-ins werden als nonreentrant angesehen.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Einschränkungen der Zeichenfolge](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)