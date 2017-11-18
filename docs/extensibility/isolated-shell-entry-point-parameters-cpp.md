---
redirect_url: shell/isolated-shell-entry-point-parameters-cpp
title: Isolierte Shell Einstiegspunktparameter (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b145207a2c74d47208df391c319f496467ae6438
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolierte Shell Einstiegspunktparameter (C++)
Wenn eine Visual Studio Shell-basierten Anwendung startet, ruft er den Ausgangspunkt der Eintrag der Visual Studio-Shell. Die folgenden Einstellungen können im Aufruf der Einstiegspunkt der Start der Shell überschrieben werden. Eine Beschreibung der einzelnen Einstellungen finden Sie [. PKGDEF Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
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
  
 Die Visual Studio Shell Isolated Vorlage erstellt eine Quelldatei *SolutionName*.cpp, in denen *SolutionName* ist der Projektmappenname für die Anwendung. Diese Datei definiert den Haupteinstiegspunkt für die Anwendung, die _tWinMain-Funktion. Diese Funktion ruft den Einstiegspunkt der Start der Shell.  
  
 Sie können das Verhalten der Anwendung ändern, indem Sie diese Einstellungen ändern, wenn die Anwendung gestartet wird.  
  
## <a name="parameters"></a>Parameter  
 Der Einstiegspunkt der Start von Visual Studio-Shell definiert fünf Parameter. Ändern Sie die ersten vier Parameter nicht. Der fünfte Parameter akzeptiert eine Liste der Einstellungen überschreiben. Der Einstiegspunkt der Start der Shell wird von den Haupteinstiegspunkt einer Anwendung aufgerufen.  
  
 Der Einstiegspunkt der Start der Shell hat die folgende Signatur.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Wenn Sie nicht möchten, lassen Sie den Wert der Einstellungen zum Überschreiben alle Anwendungseinstellungen Geben Sie Parameter als ein null-Zeiger.  
  
 Um eine oder mehrere Einstellungen zu überschreiben, übergeben Sie eine Unicodezeichenfolge, die die Einstellungen außer Kraft gesetzt werden enthält. Die Zeichenfolge ist eine durch Semikolons getrennte Liste von Name / Wert-Paaren. Jedes Paar enthält den Namen der Einstellung überschreiben, gefolgt von einem Gleichheitszeichen (=), gefolgt vom Wert der Einstellung angewendet.  
  
> [!NOTE]
>  Nehmen Sie Leerzeichen nicht in der Unicode-Zeichenfolgen aus.  
  
 Für boolesche Einstellungen stehen für die folgenden Zeichenfolgen den Wert "true"; Alle anderen Zeichenfolgen darstellen, den Wert "false". Diese Zeichenfolgen Groß-/Kleinschreibung unterschieden.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   an  
  
-   true  
  
-   ja  
  
## <a name="example"></a>Beispiel  
 Zum Deaktivieren von-add-ins und zum Ändern des Standardspeicherorts für Projekte für die Anwendung, können Sie die letzten Parameter für "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp" festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der isolierten Shells](../extensibility/customizing-the-isolated-shell.md)   
 [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)