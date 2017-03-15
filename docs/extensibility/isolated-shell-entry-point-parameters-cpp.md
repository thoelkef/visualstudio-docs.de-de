---
title: Isolierte Shell Einstiegspunkt-Parameter (C++) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolierte Shell Einstiegspunkt-Parameter (C++)
Wenn eine Visual Studio-Shell-basierten Anwendung startet, wird den Start-Einstiegspunkt der Visual Studio-Shell. Die folgenden Einstellungen können im Aufruf für den Einstiegspunkt der Start der Shell überschrieben werden. Eine Beschreibung der einzelnen Einstellungen, finden Sie unter [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   Anwendungsname  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Die Visual Studio Shell Isolated Vorlage erstellt eine Quelldatei *SolutionName*cpp, *SolutionName* ist der Projektmappenname für die Anwendung. Diese Datei definiert den Haupteinstiegspunkt für die Anwendung der _tWinMain-Funktion. Diese Funktion ruft den Einstiegspunkt der Start der Shell.  
  
 Sie können das Verhalten der Anwendung ändern, indem Sie diese Einstellungen ändern, beim Starten der Anwendung.  
  
## <a name="parameters"></a>Parameter  
 Der Start-Einstiegspunkt der Visual Studio-Shell definiert fünf Parameter. Ändern Sie die ersten vier Parameter nicht. Der fünfte Parameter hat eine Liste der Einstellungen außer Kraft setzen. Der Einstiegspunkt der Start der Shell wird von der Haupteinstiegspunkt der Anwendung aufgerufen.  
  
 Der Einstiegspunkt der Start der Shell hat folgende Signatur.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Wenn Sie nicht möchten, überschreiben alle Einstellungen, lassen den Wert der Einstellungen überschreiben Sie Parameter ein null-Zeiger.  
  
 Um eine oder mehrere Einstellungen zu überschreiben, übergeben Sie eine Unicode-Zeichenfolge mit den Einstellungen außer Kraft gesetzt werden. Die Zeichenfolge ist eine durch Semikolons getrennte Liste von Name-Wert-Paaren. Jedes Paar enthält den Namen der Einstellung überschreiben, gefolgt von einem Gleichheitszeichen (=), gefolgt vom Wert der Einstellung angewendet.  
  
> [!NOTE]
>  Leerzeichen Sie Sie keine in den Unicode-Zeichenfolgen.  
  
 Boolean-Einstellungen stehen für die folgenden Zeichenfolgen den Wert True; Alle anderen Zeichenfolgen darstellen, den Wert "false". Diese Zeichenfolgen die Groß-/Kleinschreibung.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   an  
  
-   true  
  
-   ja  
  
## <a name="example"></a>Beispiel  
 Zum Deaktivieren von Add-Ins, und Ändern des Standardspeicherorts für Projekte für Ihre Anwendung, können Sie den letzten Parameter für "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp" festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der isolierte Shells](../extensibility/customizing-the-isolated-shell.md)   
 [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
