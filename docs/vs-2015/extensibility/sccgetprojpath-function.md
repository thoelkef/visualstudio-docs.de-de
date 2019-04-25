---
title: SccGetProjPath-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4c7a4af5928f1d7b803e882c1826e451982389bc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093929"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion fordert den Benutzer einen Projektpfad, d. h. eine Zeichenfolge, die nur für das Quellcodeverwaltungs-Plug-in von Bedeutung ist. Wird aufgerufen, wenn der Benutzer ist:  
  
- Erstellen eines neuen Projekts  
  
- Hinzufügen eines vorhandenen Projekts zur Versionskontrolle  
  
- Es wird versucht, eine vorhandene Versionskontrollprojekt suchen  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpUser  
 [in, out] Den Benutzernamen (nicht zu überschreiten SCC_USER_SIZE, einschließlich des NULL-Abschlusszeichens)  
  
 lpProjName  
 [in, out] Der Name des IDE-Projekt, Projektarbeitsbereich oder Makefile (nicht zu überschreiten SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpLocalPath  
 [in, out] Der Pfad des Projekts arbeiten. Wenn `bAllowChangePath` ist `TRUE`, das Quellcodeverwaltungs-Plug-in kann diese Zeichenfolge (nicht zu, überschreitet _MAX_PATH, einschließlich des Null-Abschlusszeichens) ändern.  
  
 lpAuxProjPath  
 [in, out] Ein Puffer für den zurückgegebenen Projektpfad (nicht zu überschreiten SCC_PRJPATH_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 bAllowChangePath  
 [in] Ist dies `TRUE`, das Quellcodeverwaltungs-Plug-In können Sie zur Eingabe auffordern und Ändern der `lpLocalPath` Zeichenfolge.  
  
 pbNew  
 [in, out] Eingehenden Wert gibt an, ob ein neues Projekt erstellen. Zurückgegebene Wert gibt Erfolg zum Erstellen eines Projekts:  
  
|Eingehend|Interpretation|  
|--------------|--------------------|  
|true|Der Benutzer darf es sich um ein neues Projekt erstellen.|  
|false|Der Benutzer kann ein neues Projekt nicht erstellt werden.|  
  
|Ausgehend|Interpretation|  
|--------------|--------------------|  
|true|Ein neues Projekt erstellt wurde.|  
|false|Es wurde ein vorhandenes Projekt ausgewählt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Projekt wurde erfolgreich erstellt oder abgerufen.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|  
|SCC_E_CONNECTIONFAILURE|Es wurde ein Problem, das Quellcodeverwaltungssystem eine Verbindung herstellen möchten.|  
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Der Zweck dieser Funktion ist für die IDE, die Parameter abzurufen `lpProjName` und `lpAuxProjPath`. Nachdem das Quellcodeverwaltungs-Plug-Ins die Benutzer diese Informationen aufgefordert wird, übergibt sie diese beiden Zeichenfolgen zurück zur IDE. Diese Zeichenfolgen in der Projektmappendatei beibehalten und übergibt sie an die IDE die [SccOpenProject](../extensibility/sccopenproject-function.md) jedes Mal, wenn der Benutzer dieses Projekt öffnet. Diese Zeichenfolgen aktivieren Sie das plug-in zum Nachverfolgen von Informationen, die mit einem Projekt verknüpft sind.  
  
 Wenn die Funktion zuerst aufgerufen wird, `lpAuxProjPath` auf eine leere Zeichenfolge festgelegt ist. `lProjName` kann auch leer sein, oder sie enthält den IDE-Projektnamen, die das Quellcodeverwaltungs-Plug-in verwenden oder ignorieren können. Wenn die Funktion erfolgreich zurückgegeben wird, gibt das plug-in die beiden entsprechenden Zeichenfolgen. Die IDE keine Annahmen über diese Zeichenfolgen, werden nicht dazu verwendet werden und lässt sich nicht auf den Benutzer, sie zu ändern. Wenn der Benutzer die Einstellungen zu ändern möchte, ruft die IDE `SccGetProjPath` Übergabe in den gleichen Werten in diesem Fall wurden empfangen der letzten Ausführung. Dadurch werden die-Plug-in vollständige Kontrolle über diese zwei Zeichenfolgen.  
  
 Für `lpUser`, die IDE möglicherweise übergeben Sie einen Benutzernamen ein, oder es möglicherweise einfach übergeben eines Zeigers auf eine leere Zeichenfolge. Ist ein Benutzername, sollte das Quellcodeverwaltungs-Plug-in als Standard verwenden. Allerdings, wenn kein Name übergeben wurde, oder wenn Fehler bei der Anmeldung mit dem angegebenen Namen, den-Plug-in sollte den Benutzer auffordern für eine Anmeldung und übergeben Sie der Namen wieder `lpUser` gültigen Anmeldeinformationen empfängt. Da das plug-in dieser Zeichenfolge ändern kann, die IDE wird immer ein Puffer der Größe (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  Die erste Aktion, die die IDE führt möglicherweise ein Aufruf der `SccOpenProject` Funktion oder die `SccGetProjPath` Funktion. Daher haben beide eine identische `lpUser` -Parameter, der das Quellcodeverwaltungs-Plug-in, um die Benutzer entweder zum Zeitpunkt ermöglicht. Auch wenn die Rückgabe der Funktion ein Fehler weist darauf hin, müssen die-Plug-in dieser Zeichenfolge durch einen gültigen Anmeldenamen ausfüllen.  
  
 `lpLocalPath` ist das Verzeichnis, in dem sich der Benutzer auf das Projekt zeigt. Es kann keine leere Zeichenfolge sein. Wenn kein Verzeichnis, die aktuell definiert (wie im Falle eines Benutzers, bei dem Versuch, ein Projekt aus dem Quellcodeverwaltungssystem herunterladen) vorhanden ist und `bAllowChangePath` ist `TRUE`, das Quellcodeverwaltungs-Plug-in kann Benutzer zur Eingabe auffordern oder eine andere Methode zum Platzieren der Zeichenfolge in Besitz `lpLocalPath`. Wenn `bAllowChangePath` ist `FALSE`, das plug-in sollte nicht ändern Sie die Zeichenfolge, da der Benutzer bereits im angegebenen Verzeichnis arbeitet.  
  
 Wenn der Benutzer ein neues Projekt unter quellcodeverwaltung gestellt werden erstellt, das Quellcodeverwaltungs-Plug-in möglicherweise nicht tatsächlich erstellt es in das Quellcodeverwaltungssystem zum Zeitpunkt `SccGetProjPath` aufgerufen wird. Stattdessen werden wieder die Zeichenfolge zusammen mit einem Wert ungleich NULL für `pbNew`, gibt an, dass das Projekt in das Quellcodeverwaltungssystem erstellt wird.  
  
 Beispielsweise wenn ein Benutzer in der **neues Projekt** -Assistenten in Visual Studio fügt seinem eigenen Projekt zur quellcodeverwaltung, ruft diese Funktion von Visual Studio und das plug-in bestimmt, ob es Ordnung ist, erstellen ein neues Projekt in das Quellcodeverwaltungssystem zu enthalten Sie die Visual Studio-Projekt. Wenn der Benutzer klickt **Abbrechen** vor dem Fertigstellen des Assistenten für das Projekt wird nicht erstellt. Wenn der Benutzer klickt **OK**, ruft Visual Studio `SccOpenProject`, und übergeben Sie `SCC_OPT_CREATEIFNEW`, und das Projekt unter quellcodeverwaltung zu diesem Zeitpunkt erstellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
