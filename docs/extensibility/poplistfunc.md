---
title: "POPLISTFUNC | Microsoft Docs"
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
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "POPLISTFUNC Callback-Funktion"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Rückruf wird bereitgestellt, um die [SccPopulateList](../extensibility/sccpopulatelist-function.md) von der IDE und wird durch das Quellcodeverwaltungs\-Plug\-in verwendet, um eine Liste der Dateien oder Verzeichnisse zu aktualisieren \(auch angegeben die `SccPopulateList` Funktion\).  
  
 Wenn ein Benutzer beschließt der **abrufen** Befehl in der IDE die IDE zeigt eine Liste aller Dateien, die der Benutzer abrufen können. Die IDE weiß leider nicht genaue Liste aller Dateien, die der Benutzer erhalten möglicherweise. nur das plug\-in enthält diese Liste. Wenn andere Benutzer den Quellcode\-Verwaltungsprojekt Dateien hinzugefügt haben, sollten diese Dateien in der Liste angezeigt, aber die IDE nicht bekannt werden. Die IDE erstellt eine Liste der Dateien, die er davon ausgeht, dass der Benutzer abrufen kann. Bevor sie diese Liste für den Benutzer angezeigt wird, ruft es die [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` Kontrolle der Source\-Plug\-in eine Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste.  
  
## Signatur  
 Das Quellcodeverwaltungs\-Plug\-Ins ändert die Liste durch Aufrufen einer Funktion IDE implementiert, mit dem folgenden Prototyp:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## Parameter  
 pvCallerData  
 Die `pvCallerData` übergebene Parameter vom Aufrufer \(der IDE\) der [SccPopulateList](../extensibility/sccpopulatelist-function.md). Das Quellcodeverwaltungs\-Plug\-in sollte nichts über den Inhalt dieser Parameter angenommen werden.  
  
 fAddRemove  
 Wenn `TRUE`, `lpFileName` ist eine Datei, die der Liste hinzugefügt werden soll. Wenn `FALSE`, `lpFileName` ist eine Datei, die aus der Liste gelöscht werden soll.  
  
 nStatus  
 Status des `lpFileName` \(eine Kombination der `SCC_STATUS` Bits; Siehe [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md) Details\).  
  
 lpFileName  
 Vollständiger Pfad des Dateinamens hinzufügen oder aus der Liste löschen.  
  
## Rückgabewert  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`TRUE`|Das plug\-in kann weiterhin diese Funktion aufzurufen.|  
|`FALSE`|Auf der Seite der IDE \(z. B. eine Out\-of Arbeitsspeicher\), ist ein Problem aufgetreten. Das plug\-in sollte Vorgang zu beenden.|  
  
## Hinweise  
 Für jede Datei, die das Quellcodeverwaltungs\-Plug\-In hinzufügen oder aus der Liste löschen möchte, es diese Funktion aufruft, übergibt der `lpFileName`. Die `fAddRemove` \-Flag gibt an, eine neue Datei hinzugefügt oder die alte Datei löschen. Die `nStatus` \-Parameter gibt den Status der Datei. Wenn SCC\-Plug\-In hinzufügen und Löschen von Dateien abgeschlossen hat, gibt er aus der [SccPopulateList](../extensibility/sccpopulatelist-function.md) aufrufen.  
  
> [!NOTE]
>  Die `SCC_CAP_POPULATELIST` Funktion Bit für Visual Studio erforderlich ist.  
  
## Siehe auch  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md)