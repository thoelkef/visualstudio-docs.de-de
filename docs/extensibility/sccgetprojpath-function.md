---
title: SccGetProjPath Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetProjPath
helpviewer_keywords: SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c626cfc6da56258241071476aba03690f349092
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath-Funktion
Diese Funktion fordert den Benutzer für eine Projektpfad, d. h. eine Zeichenfolge, die nur für die Datenquellen-Steuerelement-Plug-in von Bedeutung ist. Sie wird aufgerufen, wenn der Benutzer ist:  
  
-   Erstellen eines neuen Projekts  
  
-   Ein vorhandenes Projekt hinzufügen zur Versionskontrolle  
  
-   Bei dem Versuch, ein vorhandenes Projekt der Version-Steuerelement suchen  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 [in, out] Den Benutzernamen (nicht zu überschreiten SCC_USER_SIZE, einschließlich der NULL-Terminator)  
  
 lpProjName  
 [in, out] Der Name des IDE-Projekts, Projektarbeitsbereich oder Makefile (nicht zu überschreiten SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator).  
  
 lpLocalPath  
 [in, out] Pfad für das Projekt arbeiten. Wenn `bAllowChangePath` ist `TRUE`, die Datenquellen-Steuerelement-Plug-in kann diese Zeichenfolge (nicht überschreitet _MAX_PATH, einschließlich der Null-Terminator) ändern.  
  
 lpAuxProjPath  
 [in, out] Ein Puffer für den zurückgegebenen Projektpfad (nicht zu überschreiten SCC_PRJPATH_SIZE, einschließlich der NULL-Terminator).  
  
 bAllowChangePath  
 [in] Ist dies `TRUE`, das Quellsteuerelement-Plug-In können Sie zur Eingabe und Ändern der `lpLocalPath` Zeichenfolge.  
  
 pbNew  
 [in, out] Eingehen Wert gibt an, ob ein neues Projekt erstellen. Ein Rückgabewert gibt die erfolgreiche Ausführung zum Erstellen eines Projekts:  
  
|eingehende|Interpretation|  
|--------------|--------------------|  
|true|Der Benutzer darf es sich um ein neues Projekt erstellen.|  
|false|Der Benutzer kann ein neues Projekt nicht erstellt werden.|  
  
|Ausgehend|Interpretation|  
|--------------|--------------------|  
|true|Ein neues Projekt erstellt wurde.|  
|false|Ein vorhandenes Projekt ausgewählt wurde.|  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Projekt wurde erfolgreich erstellt oder abgerufen werden.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte.|  
|SCC_E_CONNECTIONFAILURE|Es wurde ein Problem beim Versuch zur Verbindung mit des Quellcodeverwaltungssystems aus.|  
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Der Zweck dieser Funktion ist für die IDE beim Abrufen der Parameter `lpProjName` und `lpAuxProjPath`. Nachdem Sie das Quellsteuerelement-Plug-in der Benutzer zum Eingeben dieser Informationen aufgefordert werden, gibt es diese zwei Zeichenfolgen an der IDE. Die IDE weiterhin diese Zeichenfolgen in der Projektmappendatei und übergibt sie an der [SccOpenProject](../extensibility/sccopenproject-function.md) Wenn der Benutzer dieses Projekt öffnet. Diese Zeichenfolgen aktivieren Sie das plug-in zum Nachverfolgen von Informationen, die einem Projekt zugeordnet.  
  
 Wenn die Funktion zuerst aufgerufen wird, `lpAuxProjPath` auf eine leere Zeichenfolge festgelegt ist. `lProjName`kann auch leer sein, oder sie enthält die Namen der IDE-Projekt, in der die Datenquellen-Steuerelement-Plug-in verwenden oder ignorieren kann. Wenn die Funktion erfolgreich ausgeführt wurde, gibt das plug-in die beiden entsprechenden Zeichenfolgen. Die IDE trifft keine Annahmen über diese Zeichenfolgen, nicht verwendet und kann nicht der Benutzer, sie zu ändern. Wenn der Benutzer die Einstellungen zu ändern möchte, wird die IDE aufrufen `SccGetProjPath` Übergabe in die gleichen Werte erneut hat empfangen der letzten Ausführung. Dadurch werden die Plug-in-vollständige Kontrolle über diese zwei Zeichenfolgen.  
  
 Für `lpUser`, einen Benutzernamen kann die IDE übergeben oder es möglicherweise übergeben Sie einfach in einen Zeiger auf eine leere Zeichenfolge. Ist ein Benutzername, sollten die Datenquellen-Steuerelement-Plug-in als den Standardwert verwenden. Jedoch wenn kein Name übergeben wurde, oder wenn Fehler bei der Anmeldung mit dem angegebenen Namen, das plug-in sollte fragt die Benutzer nach einer Anmeldung und übergeben Sie der Namen wieder `lpUser` empfängt eine gültige Anmeldung. Da die-Plug-in dieser Zeichenfolge ändern kann, wird die IDE immer einen Puffer mit einer Größe zuweisen (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  Die erste Aktion, die von die IDE führt möglicherweise ein Aufruf der `SccOpenProject` Funktion oder die `SccGetProjPath` Funktion. Daher haben beide einen identischen `lpUser` -Parameter, der die Datenquellen-Steuerelements, das plug-in, das entweder zum Zeitpunkt der Benutzer anmelden kann. Auch wenn die Rückgabe von der Funktion ein Fehler weist darauf hin, müssen die-Plug-in dieser Zeichenfolge mit gültiger Anmeldename ausfüllen.  
  
 `lpLocalPath`ist das Verzeichnis, in dem der Benutzer das Projekt speichert. Es kann keine leere Zeichenfolge sein. Wenn es kein Verzeichnis derzeit definiert (wie im Fall eines Benutzers bei dem Versuch ist, ein Projekt aus dem Quellcodeverwaltungssystem herunterladen) und `bAllowChangePath` ist `TRUE`, die Datenquellen-Steuerelement-Plug-in zur Eingabe auffordern oder eine andere Methode verwenden, um platzieren kann dessen Zeichenfolge in besitzen `lpLocalPath`. Wenn `bAllowChangePath` ist `FALSE`, das plug-in sollte nicht ändern Sie die Zeichenfolge, da der Benutzer bereits im angegebenen Verzeichnis verwendet werden kann.  
  
 Wenn der Benutzer ein neues Projekt unter quellcodeverwaltung eingesetzt werden erstellt, die Datenquellen-Steuerelement-Plug-in möglicherweise nicht tatsächlich erstellt es in das Quellcodeverwaltungssystem zum Zeitpunkt `SccGetProjPath` aufgerufen wird. Stattdessen wird wieder die Zeichenfolge zusammen mit einem Wert ungleich NULL für `pbNew`, gibt an, dass das Projekt in das Quellcodeverwaltungssystem erstellt werden soll.  
  
 Angenommen, wenn ein Benutzer in der **neues Projekt** -Assistenten in Visual Studio fügt sein eigenes Projekt zur quellcodeverwaltung, ruft diese Funktion auf Visual Studio und das plug-in bestimmt, ob es angemessen, erstellen Sie ein neues Projekt in das Quellcodeverwaltungssystem zum ist enthalten Sie der Visual Studio-Projekt. Wenn der Benutzer klickt **"Abbrechen"** vor dem Abschluss des Assistenten für das Projekt nicht erstellt wird. Wenn der Benutzer klickt **OK**, ruft Visual Studio `SccOpenProject`, und übergeben Sie `SCC_OPT_CREATEIFNEW`, und das Quellprojekt gesteuert wird zu diesem Zeitpunkt erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)