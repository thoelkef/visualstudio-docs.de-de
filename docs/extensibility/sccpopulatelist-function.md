---
title: "SccPopulateList-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList-Funktion"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion wird eine Liste der Dateien für eine bestimmte Quelle Befehl aktualisiert und Quellcodeverwaltungsstatus für alle angegebenen Dateien bereitstellt.  
  
## Syntax  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 %nbefehl  
 \[in\] Befehl der Quelle, die auf alle Dateien angewendet, die `lpFileNames` Array \(finden Sie unter [Befehlscode](../extensibility/command-code-enumerator.md) eine Liste der möglichen Befehle\).  
  
 nFiles  
 \[in\] Anzahl der Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Ein Array von Dateinamen, die bekanntermaßen von der IDE.  
  
 pfnPopulate  
 \[in\] Die IDE\-Callback\-Funktion aufrufen, hinzufügen und Entfernen von Dateien \(siehe [POPLISTFUNC](../extensibility/poplistfunc.md) Details\).  
  
 pvCallerData  
 \[in\] Wert, der unverändert an die Rückruffunktion übergeben werden.  
  
 lpStatus  
 \[in, out\] Ein Array für das Quellcodeverwaltungs\-Plug\-in, um die Statusflags für jede Datei zurückzugeben.  
  
 Bestanden  
 \[in\] Befehl Flags \(finden Sie im Abschnitt "PopulateList Flag" [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md) Details\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Erfolgreich.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Diese Funktion überprüft die Liste der Dateien für den aktuellen Status. Er verwendet die `pfnPopulate` Rückruffunktion an den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`. Wenn der Befehl ist z. B. `SCC_COMMAND_CHECKIN` eine Datei in der Liste nicht ist ausgecheckt ist, und der Rückruf wird verwendet, um den Aufrufer darüber zu informieren. Es kann vorkommen, möglicherweise das Quellcodeverwaltungs\-Plug\-in andere Dateien, die Teil des Befehls werden konnte und hinzugefügt werden. So können z. B. einen Visual Basic\-Benutzer eine BMP\-Datei auszuchecken, die ihr Projekt werden jedoch nicht in der Visual Basic\-Projektdatei angezeigt. Ein Benutzer die **abrufen** Befehl in der IDE. Die IDE zeigt eine Liste aller Dateien, die wahrscheinlich die Benutzer erhalten, aber bevor die Liste angezeigt wird, die `SccPopulateList` Funktion wird aufgerufen, um sicherzustellen, dass die Liste anzuzeigende ist aktuell.  
  
## Beispiel  
 Die IDE erstellt eine Liste der Dateien, die er davon ausgeht, dass der Benutzer abrufen kann. Bevor dieser Liste angezeigt wird, ruft es die `SccPopulateList` \-Funktion, mit dem das Quellcodeverwaltungs\-Plug\-Ins die Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste. Das plug\-in ändert die Liste durch die angegebene Rückruffunktion aufrufen \(finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Weitere Einzelheiten\).  
  
 Rufen Sie das plug\-in weiterhin die `pfnPopulate` \-Funktion, die hinzugefügt und Dateien gelöscht, bis er abgeschlossen ist, und anschließend zurückgegeben die `SccPopulateList` Funktion. Die IDE kann dann die Liste angezeigt. Die `lpStatus` Array stellt alle Dateien in der ursprünglichen Liste von der IDE übergeben. Das plug\-in füllt den Status aller dieser Dateien zusätzlich zu machen die Callback\-Funktion verwenden.  
  
> [!NOTE]
>  Ein Quellcodeverwaltungs\-Plug\-in hat immer die Möglichkeit, die von dieser Funktion, die die Liste verlassen, wie einfach sofort zurückgegeben. Wenn ein plug\-in diese Funktion implementiert, können sie dies angeben, durch Festlegen der `SCC_CAP_POPULATELIST` Funktion Bitflag in der erste Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md). Standardmäßig sollte das plug\-in immer davon ausgehen, dass alle Elemente, die übergeben werden Dateien sind. Jedoch, wenn die IDE legt die `SCC_PL_DIR` \-flag in der `fOptions` \-Parameter sind alle Elemente, die übergeben werden Verzeichnisse anzusehen. Das plug\-in sollten Hinzufügen aller Dateien, die gehören in den Verzeichnissen. Die IDE wird nie eine Kombination von Dateien und Verzeichnissen übergeben.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)   
 [Befehlscode](../extensibility/command-code-enumerator.md)