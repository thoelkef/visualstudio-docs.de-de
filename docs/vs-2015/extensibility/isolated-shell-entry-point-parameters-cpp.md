---
title: Parameter für isolierte Shell-Einstiegspunkte (C++) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841232"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Einstiegspunktparameter für die isolierte Shell (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Shell-basierte Visual Studio-Anwendung gestartet wird, ruft Sie den Start Einstiegspunkt der Visual Studio-Shell auf. Die folgenden Einstellungen können im aufrufsstartpunkt der Shell überschrieben werden. Eine Beschreibung der einzelnen Einstellungen finden Sie unter [. Pkgdef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- Addinsallowed  
  
- Allowsdroppedfilesonmainwindow  
  
- AppName  
  
- Commandlinelogo  
  
- DefaultHomePage  
  
- Defaultprojectslocation  
  
- Defaultsearchpage  
  
- Defaultuserfilesfolderroot  
  
- Disableoutputwindow  
  
- Hidemiscellaneousfilesbydefault  
  
- Hidesolutionconcept  
  
- Newprojdlginstalledtemplateshdr  
  
- Newprojdlgslntreenodecotitle  
  
- Solutionfilekreatoridentifier  
  
- Solutionfileext  
  
- Userfilessubfoldername  
  
- Useropt fileext  
  
  Die isolierte Visual Studio Shell-Vorlage erstellt die Quelldatei " *SolutionName*. cpp", wobei " *SolutionName* " der Projektmappenname für die Anwendung ist. Diese Datei definiert den Haupteinstiegspunkt für die Anwendung, die _tWinMain Funktion. Diese Funktion Ruft den Start Einstiegspunkt der Shell auf.  
  
  Sie können das Verhalten der Anwendung ändern, indem Sie diese Einstellungen ändern, wenn die Anwendung gestartet wird.  
  
## <a name="parameters"></a>Parameter  
 Der Start Einstiegspunkt der Visual Studio Shell definiert fünf Parameter. Ändern Sie die ersten vier Parameter nicht. Der fünfte Parameter nimmt eine Einstellungs Überschreibungs Liste an. Der Start Einstiegspunkt der Shell wird vom Haupteinstiegspunkt einer Anwendung aus aufgerufen.  
  
 Der Start Einstiegspunkt der Shell hat die folgende Signatur.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Wenn Sie keine Anwendungseinstellungen außer Kraft setzen möchten, belassen Sie den Wert des Parameters Einstellungen überschreiben als NULL-Zeiger.  
  
 Um eine oder mehrere Einstellungen zu überschreiben, übergeben Sie eine Unicode-Zeichenfolge, die die Einstellungen enthält, die überschrieben werden sollen. Die Zeichenfolge ist eine durch Semikolons getrennte Liste von Name-Wert-Paaren. Jedes Paar enthält den Namen der zu über schreibenden Einstellung, gefolgt von einem Gleichheitszeichen (=), gefolgt von dem Wert, der auf die Einstellung angewendet werden soll.  
  
> [!NOTE]
> Fügen Sie keine Leerzeichen in die Unicode-Zeichen folgen ein.  
  
 Für boolesche Einstellungen stellen die folgenden Zeichen folgen den Wert true dar. alle anderen Zeichen folgen stellen den Wert false dar. Diese Zeichen folgen Unterscheidung nach Groß-/Kleinschreibung.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- ja  
  
## <a name="example"></a>Beispiel  
 Wenn Sie Add-Ins deaktivieren und den Speicherort der Standardprojekte für Ihre Anwendung ändern möchten, können Sie den letzten Parameter auf "addinsallowed = false; defaultprojectslocation =%USERPROFILE%\temp" festlegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen der isolierten Shell](../extensibility/customizing-the-isolated-shell.md)   
 [PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
