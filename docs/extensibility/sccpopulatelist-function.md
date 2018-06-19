---
title: SccPopulateList Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26e7bbb4a99c3cd649eedb7638feb5b6170b3b59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140290"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList-Funktion
Diese Funktion wird eine Liste der Dateien für eine bestimmte Quelle steuerungsbefehls aktualisiert und Source Control Status für alle angegebenen Dateien bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 %nbefehl  
 [in] Die Quelle steuerungsbefehls, die für alle Dateien im angewendet werden die `lpFileNames` Array (finden Sie unter [Befehlscode](../extensibility/command-code-enumerator.md) eine Liste der möglichen Befehle).  
  
 nFiles  
 [in] Anzahl der Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 [in] Ein Array von Dateinamen, die bekanntermaßen von der IDE.  
  
 pfnPopulate  
 [in] Die IDE Callback-Funktion aufrufen, hinzufügen und Entfernen von Dateien (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Einzelheiten).  
  
 pvCallerData  
 [in] Wert, der unverändert an die Rückruffunktion übergeben werden.  
  
 lpStatus  
 [in, out] Ein Array für die Datenquellen-Steuerelement-Plug-in die Statusflags für jede Datei zurückzugeben.  
  
 fOptions  
 [in] Befehl Flags (finden Sie im Abschnitt "PopulateList Flag" [Bitflags verwendet wird, indem Sie bestimmte Befehle](../extensibility/bitflags-used-by-specific-commands.md) Einzelheiten).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolgreich.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion überprüft die Liste der Dateien für den aktuellen Status an. Er verwendet die `pfnPopulate` Rückruffunktion an den Aufrufer benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`. Wenn der Befehl ist z. B. `SCC_COMMAND_CHECKIN` eine Datei in der Liste ist nicht ausgecheckt, und der Rückruf wird verwendet, um den Aufrufer darüber zu informieren. In einigen Fällen möglicherweise das Quellsteuerelement-Plug-in andere Dateien, die Teil des Befehls werden könnte, und fügen Sie diese hinzu. Dadurch kann beispielsweise einen Visual Basic-Benutzer, auszuchecken, BMP-Datei, die ist sein eigenes Projekt verwendeten, aber nicht in der Visual Basic-Projektdatei angezeigt. Ein Benutzer wählt die **abrufen** Befehl in der IDE. Die IDE zeigt eine Liste aller Dateien, die der Benutzer erhalten werden wahrscheinlich, jedoch vor die Liste angezeigt wird, die `SccPopulateList` Funktion wird aufgerufen, um sicherzustellen, dass die Liste angezeigt wird, werden auf dem neuesten Stand ist.  
  
## <a name="example"></a>Beispiel  
 Die IDE erstellt eine Liste der Dateien, die wahrscheinlich, dass der Benutzer abrufen kann. Bevor sie dieser Liste angezeigt wird, ruft die `SccPopulateList` -Funktion, mit der quellcodeverwaltung-Plug-in die Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste. Das plug-in ändert die Liste durch Aufrufen der Rückruffunktion angegebenen (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Weitere Details).  
  
 Rufen Sie das plug-in weiterhin die `pfnPopulate` -Funktion, die hinzufügt und löscht Dateien, bis er abgeschlossen ist, und gibt dann aus der `SccPopulateList` Funktion. Die IDE können Sie die Liste anzeigen. Die `lpStatus` Array alle Dateien in der ursprünglichen Liste, die von der IDE übergebenen darstellt. Verwenden Sie die Plug-in-füllt den Status aller dieser Dateien darüber hinaus machen der Rückruffunktion.  
  
> [!NOTE]
>  Ein Quellcodeverwaltungs-Plug-in hat immer die Möglichkeit, umgehend aus dieser Funktion, lassen die Liste unverändert zurückgeben. Wenn ein plug-in dieser Funktion implementiert, können sie dies angeben, durch Festlegen der `SCC_CAP_POPULATELIST` Funktion Bitflags im ersten Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md). Standardmäßig sollten das plug-in immer davon ausgehen, dass alle Elemente im übergebenen Dateien befinden. Jedoch wenn die IDE legt die `SCC_PL_DIR` -flag in der `fOptions` Parameter, alle Elemente, die übergeben werden Verzeichnisse angesehen werden. Das plug-in sollten Hinzufügen aller Dateien, die gehören in den Verzeichnissen. Die IDE übergeben, wird nie in eine Mischung von Dateien und Verzeichnisse.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)   
 [Befehls-Code](../extensibility/command-code-enumerator.md)