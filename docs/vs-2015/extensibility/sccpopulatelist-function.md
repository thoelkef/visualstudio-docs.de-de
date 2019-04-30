---
title: SccPopulateList-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5efdddc448dc8e04ee963eaa1b342a93666d9b62
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446775"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion eine Liste der Dateien für einen bestimmten Quell-Steuerelement-Befehl aktualisiert und Status der quellcodeverwaltung für alle angegebenen Dateien bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 %nbefehl  
 [in] Der Befehl "Quelle-Steuerelement", die für alle Dateien im angewendet werden, die `lpFileNames` Array (finden Sie unter [Befehlscode](../extensibility/command-code-enumerator.md) eine Liste der möglichen Befehle).  
  
 nFiles  
 [in] Anzahl der Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Ein Array von Dateinamen, die bekanntermaßen von der IDE.  
  
 pfnPopulate  
 [in] Die IDE-Callback-Funktion aufrufen, zum Hinzufügen und Entfernen von Dateien (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Einzelheiten).  
  
 pvCallerData  
 [in] Wert, der unverändert an die Rückruffunktion übergeben werden soll.  
  
 lpStatus  
 [in, out] Ein Array für das Quellcodeverwaltungs-Plug-in, um die Statusflags für jede Datei zurückzugeben.  
  
 Bestanden  
 [in] Befehl Flags (finden Sie im Abschnitt "PopulateList Flag" [Bitflags, die von bestimmten Befehlen verwendete](../extensibility/bitflags-used-by-specific-commands.md) Einzelheiten).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolgreich.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion untersucht die Liste der Dateien für den aktuellen Status. Er verwendet die `pfnPopulate` Rückruffunktion, die den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`. Wenn der Befehl ist z. B. `SCC_COMMAND_CHECKIN` eine Datei in der Liste ist nicht ausgecheckt, und der Rückruf wird verwendet, um den Aufrufer darüber zu informieren. In einigen Fällen möglicherweise das Quellcodeverwaltungs-Plug-in andere Dateien, die Teil des Befehls werden konnte, und fügen sie hinzu. Dies kann beispielsweise einen Visual Basic-Benutzer eine BMP-Datei auschecken, die wird von seinem eigenen Projekt verwendet, aber nicht in der Visual Basic-Projektdatei angezeigt. Ein Benutzer wählt die **erhalten** Befehl in der IDE. Die IDE zeigt eine Liste aller Dateien, die sie annimmt, der Benutzer erhalten dass, aber bevor die Liste angezeigt wird, die `SccPopulateList` Funktion wird aufgerufen, um sicherzustellen, dass die Liste angezeigt wird, werden auf dem neuesten Stand ist.  
  
## <a name="example"></a>Beispiel  
 Die IDE erstellt eine Liste der Dateien, die er davon ausgeht, dass der Benutzer abrufen kann. Bevor sie dieser Liste angezeigt wird, ruft es die `SccPopulateList` Funktion, mit dem das Quellcodeverwaltungs-Plug-Ins die Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste. Das plug-in ändert die Liste durch Aufrufen der angegebenen Rückruffunktion (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Weitere Details).  
  
 Rufen Sie das plug-in weiterhin die `pfnPopulate` Funktion, die hinzugefügt und werden die Dateien, gelöscht, bis sie abgeschlossen ist, und gibt dann zurück, aus der `SccPopulateList` Funktion. Die IDE kann dann die Liste angezeigt. Die `lpStatus` Array stellt alle Dateien in der ursprünglichen Liste, die von der IDE übergebenen dar. Die Callback-Funktion verwenden die-Plug-in fügt automatisch den Status aller dieser Dateien zudem zu machen.  
  
> [!NOTE]
> Ein Quellcodeverwaltungs-Plug-in verfügt immer über die Möglichkeit, die umgehend von dieser Funktion, verlassen die Liste unverändert zurückgeben. Wenn ein plug-in diese Funktion implementiert, können sie dies angeben, durch Festlegen der `SCC_CAP_POPULATELIST` Funktion Bitflag in der erste Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md). Standardmäßig sollten das plug-in immer davon ausgehen, dass alle Elemente übergeben werden Dateien sind. Jedoch, wenn die IDE legt die `SCC_PL_DIR` -flag in der `fOptions` -Parameter sind, dass alle Elemente übergeben werden Verzeichnisse berücksichtigt werden. Das plug-in sollten hinzufügen, alle Dateien, die gehören in den Verzeichnissen. Die IDE wird nie eine Mischung von Dateien und Verzeichnissen übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)   
 [Befehlscode](../extensibility/command-code-enumerator.md)
