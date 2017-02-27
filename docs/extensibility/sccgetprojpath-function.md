---
title: "SccGetProjPath-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetProjPath"
helpviewer_keywords: 
  - "SccGetProjPath-Funktion"
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccGetProjPath-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion fordert den Benutzer für eine Projektpfad, d. h. eine Zeichenfolge, die nur für das Quellcodeverwaltungs\-Plug\-in von Bedeutung ist. Sie wird aufgerufen, wenn der Benutzer ist:  
  
-   Erstellen eines neuen Projekts  
  
-   Ein vorhandenes Projekt hinzufügen zur Versionskontrolle  
  
-   Bei dem Versuch, eine vorhandene Versionskontrollprojekt suchen  
  
## Syntax  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 \[in, out\] Der Benutzername \(nicht zu überschreiten SCC\_USER\_SIZE, einschließlich des NULL\-Abschlusszeichens\)  
  
 lpProjName  
 \[in, out\] Der Name des IDE\-Projekts, Project\-Arbeitsbereich oder Makefile \(nicht zu überschreiten SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 lpLocalPath  
 \[in, out\] Pfad für das Projekt arbeiten. Wenn `bAllowChangePath` ist `TRUE`, das Quellcodeverwaltungs\-Plug\-in kann diese Zeichenfolge \(nicht zu überschreiten \_MAX\_PATH, einschließlich des Null\-Abschlusszeichens\) ändern.  
  
 lpAuxProjPath  
 \[in, out\] Ein Puffer für den zurückgegebenen Projektpfad \(nicht zu überschreiten SCC\_PRJPATH\_SIZE, einschließlich des NULL\-Abschlusszeichens\).  
  
 bAllowChangePath  
 \[in\] Ist dies `TRUE`, das Quellcodeverwaltungs\-Plug\-In können Sie anfordern und ändern die `lpLocalPath` Zeichenfolge.  
  
 pbNew  
 \[in, out\] Eingehenden Wert gibt an, ob ein neues Projekt erstellen. Zurückgegebene Wert gibt Erfolg ein Projekts zu erstellen:  
  
|Eingehende|Interpretation|  
|----------------|--------------------|  
|TRUE|Der Benutzer kann ein neues Projekt erstellen.|  
|FALSE|Der Benutzer kann nicht auf ein neues Projekt erstellen.|  
  
|Ausgehend|Interpretation|  
|---------------|--------------------|  
|TRUE|Ein neues Projekt erstellt wurde.|  
|FALSE|Ein vorhandenes Projekt ausgewählt wurde.|  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Das Projekt wurde erfolgreich erstellt oder abgerufen.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte.|  
|SCC\_E\_CONNECTIONFAILURE|Es wurde ein Problem mit dem Quellcode\-Verwaltungssystem eine Verbindung herstellen möchten.|  
|SCC\_E\_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## Hinweise  
 Der Zweck dieser Funktion ist für die IDE, erhalten die Parameter `lpProjName` und `lpAuxProjPath`. Nachdem das Quellcodeverwaltungs\-Plug\-in dieser Informationen den Benutzer auffordert, übergibt es diese beiden Zeichenfolgen zurück zur IDE. Die IDE speichert diese Zeichenfolgen in die Projektmappendatei und übergibt sie an die [SccOpenProject](../extensibility/sccopenproject-function.md) jedes Mal, wenn der Benutzer dieses Projekt geöffnet. Diese Zeichenfolgen aktivieren Sie das plug\-in zum Nachverfolgen von Informationen, die einem Projekt zugeordnet.  
  
 Wenn die Funktion erstmalig aufgerufen wird, `lpAuxProjPath` auf eine leere Zeichenfolge festgelegt ist.`lProjName` kann auch leer sein, oder sie enthält den IDE\-Projektnamen, die das Quellcodeverwaltungs\-Plug\-in verwenden oder ignorieren können. Wenn die Funktion erfolgreich ausgeführt wurde, gibt das plug\-in die beiden entsprechenden Zeichenfolgen. Die IDE keine Annahmen über diese Zeichenfolgen, nicht verwenden und nicht zugelassen, dass den Benutzer diese ändern. Wenn der Benutzer die Einstellungen zu ändern möchte, wird die IDE aufrufen `SccGetProjPath` erneut in die gleichen Werte übergeben hatte empfangen, den Zeitpunkt der vorherigen. Dadurch wird die plug\-in vollständige Kontrolle über diese zwei Zeichenfolgen.  
  
 Für `lpUser`, die IDE möglicherweise einen Benutzernamen übergeben oder es kann einfach übergeben Sie einen Zeiger auf eine leere Zeichenfolge. Wenn ein Benutzername vorhanden ist, sollten das Quellcodeverwaltungs\-Plug\-in als Standard verwenden. Jedoch, wenn kein Name übergeben wurde, oder wenn Fehler bei der Anmeldung mit dem angegebenen Namen, das plug\-in sollte den Benutzer auffordern für eine Anmeldung und übergeben Sie der Namen wieder `lpUser` eine gültige Anmeldung empfängt. Da das plug\-in diese Zeichenfolge geändert werden kann, die IDE immer einen Puffer der Größe zuzuordnen \(`SCC_USER_LEN`\+ 1\).  
  
> [!NOTE]
>  Die erste Aktion, die die IDE führt möglicherweise ein Aufruf der `SccOpenProject` \-Funktion oder `SccGetProjPath` Funktion. Daher haben beide eine identische `lpUser` \-Parameter, der das Datenquellen\-Steuerelement, das plug\-in, das entweder zum Zeitpunkt der Benutzer anmelden kann. Auch wenn die Rückgabe der Funktion ein Fehler weist darauf hin, müssen das plug\-in dieser Zeichenfolge durch einen gültigen Benutzernamen eingeben.  
  
 `lpLocalPath` ist das Verzeichnis, in dem der Benutzer das Projekt speichert. Es kann keine leere Zeichenfolge sein. Es ist kein Verzeichnis \(wie im Falle ein Benutzer versucht, ein Projekt aus dem Quellcode\-Verwaltungssystem herunterzuladen\) derzeit definiert und `bAllowChangePath` ist `TRUE`, das Quellcodeverwaltungs\-Plug\-in kann Benutzer zur Eingabe auffordern oder verwenden Sie eine andere Methode um eine eigene Zeichenfolge in `lpLocalPath`. Wenn `bAllowChangePath` ist `FALSE`, das plug\-in sollte nicht ändern Sie die Zeichenfolge, da der Benutzer bereits im angegebenen Verzeichnis arbeitet.  
  
 Wenn der Benutzer ein neues Projekt unter Versionskontrolle zu versetzen erstellt, das Quellcodeverwaltungs\-Plug\-in erstellen u. u. nicht tatsächlich es im Quellcode\-Verwaltungssystem zum Zeitpunkt `SccGetProjPath` aufgerufen wird. Stattdessen wird wieder die Zeichenfolge zusammen mit einem Wert ungleich NULL für `pbNew`, gibt an, dass das Projekt in das Quellcodeverwaltungssystem erstellt wird.  
  
 Beispielsweise, wenn ein Benutzer in der **Neues Projekt** \-Assistenten in Visual Studio fügt seinem eigenen Projekt zur Versionskontrolle, ruft diese Funktion auf Visual Studio und das plug\-in bestimmt, ob es zum Erstellen eines neuen Projekts in Quellcode\-Verwaltungssystem, das Visual Studio\-Projekt enthalten ist. Wenn der Benutzer klickt **Abbrechen** vor Beendigung des Assistenten für das Projekt nicht erstellt. Klickt der Benutzer **OK**, ruft Visual Studio `SccOpenProject`, wobei `SCC_OPT_CREATEIFNEW`, und das Quellprojekt gesteuert wird zu diesem Zeitpunkt erstellt.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)