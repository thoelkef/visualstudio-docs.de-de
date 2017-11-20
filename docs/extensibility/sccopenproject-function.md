---
title: SccOpenProject Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccOpenProject
helpviewer_keywords: SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d61b4fade0775c5e017a85fa5364779bc567b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccopenproject-function"></a>SccOpenProject-Funktion
Diese Funktion öffnet ein vorhandenes Projekt des Datenquellen-Steuerelement oder ein neues Zertifikat erstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 [in, out] Der Name des Benutzers (nicht zu überschreiten SCC_USER_SIZE, einschließlich der NULL-Terminator).  
  
 lpProjName  
 [in] Die Zeichenfolge, die den Namen des Projekts zu identifizieren.  
  
 lpLocalProjPath  
 [in] Der Pfad zu den Arbeitsordner für das Projekt.  
  
 lpAuxProjPath  
 [in, out] Eine optionale zusätzlichen Zeichenfolge, die das Projekt (nicht zu überschreiten SCC_AUXPATH_SIZE, einschließlich der NULL-Terminator) zu identifizieren.  
  
 lpComment  
 [in] Kommentar zu einem neuen Projekt, das erstellt wird.  
  
 lpTextOutProc  
 [in] Eine optionale Rückruffunktion zum Anzeigen von Text, die Ausgabe aus der quellcodeverwaltung-Plug-in.  
  
 dwFlags  
 [in] Signale steuern, ob ein neues Projekt muss erstellt werden, wenn das Projekt an der Quelle unbekannt ist-Plug-in. Wert kann eine Kombination von `SCC_OP_CREATEIFNEW` und`SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolg beim Öffnen des Projekts.|  
|SCC_E_INITIALIZEFAILED|Projekt konnte nicht initialisiert werden.|  
|SCC_E_INVALIDUSER|Der Benutzer konnte nicht vom Quellcodeverwaltungssystem anmelden.|  
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt vor dem Aufruf nicht vorhanden.  die `SCC_OPT_CREATEIFNEW` Flag festgelegt wurde, aber das Projekt konnte nicht erstellt werden.|  
|SCC_E_PROJSYNTAXERR|Ungültige Syntax.|  
|SCC_E_UNKNOWNPROJECT|Das Projekt ist unbekannt, das Datenquellen-Steuerelement-Plug-in, und die `SCC_OPT_CREATEIFNEW` Flag nicht festgelegt wurde.|  
|SCC_E_INVALIDFILEPATH|Das Dateipfad ist ungültig oder kann nicht verwendet werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECFICERROR|Ein unspezifischen Fehlers; das Quellcodeverwaltungssystem wurde nicht initialisiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE möglicherweise übergeben Sie einen Benutzernamen (`lpUser`), oder es kann übergeben Sie einfach in einen Zeiger auf eine leere Zeichenfolge. Ist ein Benutzername, sollten die Datenquellen-Steuerelement-Plug-in als den Standardwert verwenden. Jedoch, wenn kein Name übergeben wurde oder wenn Fehler bei der Anmeldung mit dem angegebenen Namen, das plug-in sollte der Benutzer aufgefordert, melden Sie sich und zurück in den gültigen Namen `lpUser` empfängt eine gültige Anmeldung`.` , da die Benutzernamen-Zeichenfolge des Plug-Ins ändern kann , die IDE belegt immer einen Puffer mit einer Größe (`SCC_USER_LEN`+ 1 oder SCC_USER_SIZE, die Speicherplatz für das Nullabschlusszeichen enthält).  
  
> [!NOTE]
>  Die erste Aktion die IDE möglicherweise erforderlich, um durchzuführen ist möglicherweise ein Aufruf der `SccOpenProject` Funktion oder die [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Aus diesem Grund haben beide einen identischen `lpUser` Parameter.  
  
 `lpAuxProjPath`und`lpProjName` sind die Projektmappendatei auslesen oder von einem Aufruf ausgegeben werden die `SccGetProjPath` Funktion. Diese Parameter enthalten die Zeichenfolgen, die das Projekt der quellcodeverwaltung-Plug-in zugeordnet und werden nur für das angegebene plug-in verwertbar. Wenn kein solcher Zeichenfolgen in der Projektmappendatei sind und der Benutzer hat nicht durchsuchen aufgefordert wurde (würde die eine Zeichenfolge durch Zurückgeben der `SccGetProjPath` Funktion), die IDE transferiert leere Zeichenfolgen für beide `lpAuxProjPath` und `lpProjName`, und erwartet, dass diese Werte aktualisiert werden Diese Funktion gibt, durch die When-Plug-in.  
  
 `lpTextOutProc`ist ein Zeiger auf eine Rückruffunktion, die von der IDE auf die Datenquellen-Steuerelement-Plug-In für die Anzeige von Ausgabe des Befehls Ergebnis bereitgestellt. Dieser Rückruffunktion wird ausführlich beschrieben unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Beabsichtigt das Quellsteuerelement-Plug-in profitieren, es muss festgelegt werden die `SCC_CAP_TEXTOUT` -flag in der [SccInitialize](../extensibility/sccinitialize-function.md). Wenn dieses Flag nicht festgelegt wurde, oder wenn die IDE, diese Funktion nicht unterstützt `lpTextOutProc` werden `NULL`.  
  
 Die `dwFlags` Parameter steuert das Ergebnis, wenn das Projekt geöffnet, die derzeit nicht vorhanden ist. Er besteht aus zwei Bitflags `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN`. Wenn das Projekt geöffnet, die bereits vorhanden ist, die Funktion wird das Projekt geöffnet und gibt `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` Flag ist auf, die Datenquellen-Steuerelement-Plug-in Erstellen des Projekts in das Quellcodeverwaltungssystem, öffnen Sie ihn und zurückgeben kann `SCC_OK`. Wenn das Projekt nicht vorhanden ist und die `SCC_OP_CREATEIFNEW` Flag ist deaktiviert, das plug-in sollte überprüfen Sie, ob die `SCC_OP_SILENTOPEN` Flag. Wenn dieses Flag nicht aktiviert ist, kann das plug-in den Benutzer für einen Projektnamen aufgefordert. Wenn dieses Flag aktiviert ist, das plug-in sollte einfach zurückgeben `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Aufrufen der Reihenfolge  
 Des normalen Betriebs der Ereignisse die [SccInitialize](../extensibility/sccinitialize-function.md) würde zuerst aufgerufen werden, um eine Quelle Steuerelement-Sitzung zu öffnen. Eine Sitzung besteht möglicherweise aus einem Aufruf von `SccOpenProject`, gefolgt von einer anderen Quelle Steuerelement-Plug-in-API-Funktionsaufrufe ein, und endet mit einem Aufruf von der [SccCloseProject](../extensibility/scccloseproject-function.md). Solche Sitzungen können wiederholt werden, mehrmals vor der [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Wenn die Quelle-Plug-in Sätze steuern die `SCC_CAP_REENTRANT` bit im `SccInitialize`, und klicken Sie dann die oben angegebene Reihenfolge für die Sitzung parallel mehrfach wiederholt werden kann. Verschiedene `pvContext` Strukturen nachverfolgen, die anderen Sitzungen, in denen die einzelnen `pvContext` zu einem Zeitpunkt mit einem geöffneten Projekt verknüpft ist. Auf der Grundlage der`pvContext` Parameter, das plug-in können bestimmen, welches Projekt in keinem bestimmten Aufruf verwiesen wird. Wenn die Funktion bit `SCC_CAP_REENTRANT` nicht festgelegt ist, nonreentrant Source Control-Plug-ins in ihrer Fähigkeit zum Arbeiten mit mehreren Projekten beschränkt sind.  
  
> [!NOTE]
>  Die `SCC_CAP_REENTRANT` Bit wurde in Version 1.1 von der Quelle Steuerelement-Plug-in-API eingeführt. Es ist nicht festgelegt oder ist in Version 1.0 ignoriert, und alle Version 1.0 Source Control-Plug-ins werden als nonreentrant angesehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Einschränkungen für Zeichenfolgenlängen](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)