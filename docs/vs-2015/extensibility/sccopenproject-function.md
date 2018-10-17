---
title: SccOpenProject-Funktion | Microsoft-Dokumentation
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
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2118d6ed43355d6882c1c2034388f3c438a5a6f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264380"
---
# <a name="sccopenproject-function"></a>SccOpenProject-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion öffnet ein vorhandenes Projekt des Datenquellen-Steuerelement oder eine neue erstellt.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpUser  
 [in, out] Der Name des Benutzers (nicht zu überschreiten SCC_USER_SIZE, einschließlich des NULL-Abschlusszeichens).  
  
 lpProjName  
 [in] Die Zeichenfolge, die den Namen des Projekts identifiziert.  
  
 lpLocalProjPath  
 [in] Der Pfad zu den Arbeitsordner für das Projekt.  
  
 lpAuxProjPath  
 [in, out] Eine optionale zusätzliche Zeichenfolge, die das Projekt (nicht zu überschreiten SCC_AUXPATH_SIZE, einschließlich des NULL-Abschlusszeichens) identifizieren.  
  
 lpComment  
 [in] Kommentar zu einem neuen Projekt, das erstellt wird.  
  
 lpTextOutProc  
 [in] Eine optionale Rückruffunktion zum Anzeigen von Text, der das Quellcodeverwaltungs-Plug-in die Ausgabe.  
  
 dwFlags  
 [in] Signalisiert, ob ein neues Projekt muss erstellt werden, wenn das Projekt die Quelle nicht bekannt ist-Steuerelement-Plug-in. Wert kann eine Kombination von sein `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolg des Projekts zu öffnen.|  
|SCC_E_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte nicht vom Quellcodeverwaltungssystem Anmeldung.|  
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt vor dem Aufruf nicht vorhanden.  die `SCC_OPT_CREATEIFNEW` Flag festgelegt wurde, aber das Projekt konnte nicht erstellt werden.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_UNKNOWNPROJECT|Das Projekt das Quellcodeverwaltungs-Plug-in, nicht bekannt ist und die `SCC_OPT_CREATEIFNEW` Flag nicht festgelegt wurde.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECFICERROR|Einem nicht spezifischen Fehler; der Quellcode-Verwaltungssystems wurde nicht initialisiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE möglicherweise übergeben Sie einen Benutzernamen (`lpUser`), oder es kann einfach in einen Zeiger auf eine leere Zeichenfolge. Ist ein Benutzername, sollte das Quellcodeverwaltungs-Plug-in als Standard verwenden. Allerdings, wenn kein Name übergeben wurde, oder Fehler bei der Anmeldung mit dem angegebenen Namen, das plug-in muss der Benutzer aufgefordert, melden Sie sich und gibt den gültigen Namen in `lpUser` empfängt eine gültige Anmeldung`.` , da das plug-in die Benutzernamen-Zeichenfolge ändern kann , die IDE wird immer ein Puffer der Größe (`SCC_USER_LEN`+ 1 oder SCC_USER_SIZE, die Speicherplatz für das Nullabschlusszeichen enthält).  
  
> [!NOTE]
>  Die erste Aktion, die die IDE möglicherweise erforderlich, führen Sie möglicherweise einen Aufruf der `SccOpenProject` Funktion oder die [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Aus diesem Grund haben beide eine identische `lpUser` Parameter.  
  
 `lpAuxProjPath` und`lpProjName` werden aus der Projektmappendatei gelesen oder diese von einem Aufruf zurückgegeben werden die `SccGetProjPath` Funktion. Dieser Parameter enthält die Zeichenfolgen, die das Projekt das Quellcodeverwaltungs-Plug-in zugeordnet und nur für das plug-in von Bedeutung sind. Wenn kein solcher Zeichenfolgen, in der Projektmappendatei sind und der Benutzer nicht aufgefordert wurde, navigieren Sie (die eine Zeichenfolge über zurück der `SccGetProjPath` Funktion), die IDE transferiert leere Zeichenfolgen für beide `lpAuxProjPath` und `lpProjName`, und erwartet, dass diese Werte aktualisiert werden durch die When-Plug-in diese Funktion gibt.  
  
 `lpTextOutProc` ist ein Zeiger auf eine Rückruffunktion, die von der IDE auf das Quellcodeverwaltungs-Plug-In für die Anzeige von Ausgabe des Befehls Ergebnis bereitgestellt. Diese Callback-Funktion wird ausführlich beschrieben [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Wenn das Quellcodeverwaltungs-Plug-in dies nutzen soll, es muss festgelegt werden die `SCC_CAP_TEXTOUT` -flag in der [SccInitialize](../extensibility/sccinitialize-function.md). Wenn dieses Flag nicht festgelegt wurde, oder wenn die IDE nicht mit dieser Funktion unterstützt `lpTextOutProc` werden `NULL`.  
  
 Die `dwFlags` Parameter steuert das Ergebnis aus, die das Projekt geöffnet wird derzeit nicht vorhanden ist. Es besteht aus zwei Bitflags, `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN`. Wenn das Projekt geöffnet wird, bereits vorhanden ist, die Funktion einfach Öffnet das Projekt und gibt `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` Flag ist auf, das Quellcodeverwaltungs-Plug-in Erstellen des Projekts in das Quellcodeverwaltungssystem, öffnen Sie es und zurückgeben kann `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` deaktiviert ist, das plug-in muss und suchen Sie nach der `SCC_OP_SILENTOPEN` Flag. Wenn dieses Flag nicht aktiviert ist, kann das plug-in der Benutzer einen Projektnamen aufgefordert. Ist dieses Flag auf, das plug-in muss einfach zurückgeben `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Aufrufreihenfolge  
 Während des normalen von Ereignissen die [SccInitialize](../extensibility/sccinitialize-function.md) wird zuerst aufgerufen werden, um eine Source-Control-Sitzung öffnen. Eine Sitzung möglicherweise bestehen aus einem Aufruf von `SccOpenProject`, gefolgt von anderen Source Control-Plug-in-API-Funktionsaufrufe und endet mit einem Aufruf der [SccCloseProject](../extensibility/scccloseproject-function.md). Diese Sitzungen mehrmals vor dem wiederholt werden die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Wenn die Quelle-Plug-in Gruppen steuern die `SCC_CAP_REENTRANT` bit im `SccInitialize`, und klicken Sie dann die oben angegebene Reihenfolge für die Sitzung parallel mehrmals wiederholt werden kann. Verschiedene `pvContext` Strukturen nachverfolgen, die anderen Sitzungen, in denen die einzelnen `pvContext` jeweils mit einem geöffneten Projekt zugeordnet ist. Auf der Grundlage der`pvContext` -Parameter des Plug-Ins können bestimmen, welches Projekt in einem bestimmten Aufruf verwiesen wird. Wenn die Funktion bit `SCC_CAP_REENTRANT` nicht festgelegt ist, nonreentrant Quellcodeverwaltungs-Plug-ins sind in der Lage, arbeiten mit mehreren Projekten beschränkt.  
  
> [!NOTE]
>  Die `SCC_CAP_REENTRANT` Bit wurde in Version 1.1 von der Quelle-Plug-in-API eingeführt. Es ist nicht festgelegt oder wird in Version 1.0 ignoriert, und alle Version 1.0 Quellcodeverwaltungs-Plug-ins wird angenommen, dass nonreentrant.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Einschränkungen der Zeichenfolge](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

