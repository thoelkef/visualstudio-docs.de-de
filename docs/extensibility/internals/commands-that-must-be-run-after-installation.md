---
title: "Befehle, die nach der Installation ausgef&#252;hrt werden m&#252;ssen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nach Abschluss der Installation Befehle"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Befehle, die nach der Installation ausgef&#252;hrt werden m&#252;ssen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie die Erweiterung über eine MSI\-Datei bereitstellen, müssen Sie ausführen `Devenv/Setup` als Teil der Installation in der Reihenfolge für Visual Studio Ihre Erweiterungen zu ermitteln.  
  
> [!NOTE]
>  Die Informationen in diesem Thema gelten für Suchen DevEnv mit Visual Studio 2008 und früheren Versionen von. Informationen zum Ermitteln von DevEnv mit einer neueren Version von Visual Studio finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
## Suchen von devenv.exe  
 Jede Version finden Sie devenv.exe aus der Registrierung Werte, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installationsprogramme schreiben, verwenden die RegLocator\-Tabelle und die AppSearch\-Tabelle Registrierungswerte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
### RegLocator Tabellenzeilen devenv.exe aus unterschiedlichen Versionen von Visual Studio zu suchen.  
  
|Signature\_|Stammverzeichnis|Taste|Name|Typ|  
|-----------------|----------------------|-----------|----------|---------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### AppSearch Tabellenzeilen für die entsprechende RegLocator Tabellenzeilen  
  
|Eigenschaft|Signature\_|  
|-----------------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 Visual Studio\-Installationsprogramm schreibt z. B. den Wert des Registrierungsschlüssels, der **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** als **C:\\VS2008\\Common7\\IDE\\devenv.exe**, einen vollständigen Pfad der ausführbaren Datei, die das Installationsprogramm ausführen muss.  
  
 **Hinweis** da RegLocator Typspalte 2 ist, ist es nicht notwendig, die zusätzliche Versionsinformationen in der Signatur Tabelle angeben.  
  
## Ausführen von devenv.exe  
 Nach der AppSearch Standardaktionen im Installationsprogramm ausgeführt wird, hat jede Eigenschaft in der Tabelle AppSearch Wert verweist auf die Datei "devenv.exe" für die entsprechende Version von Visual Studio. Wenn der angegebene Registrierungswert nicht vorhanden sind –, da diese Version von Visual Studio nicht installiert ist – die angegebene Eigenschaft ist festgelegt auf Null.  
  
 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, die auf eine Eigenschaft durch benutzerdefinierte Aktion geben Sie 50 ein. Die benutzerdefinierte Aktion aufzunehmen, die im Skript Ausführungsoptionen MsidbCustomActionTypeInScript \(1024\) und MsidbCustomActionTypeCommit \(512\), um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor Sie dessen Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter CustomAction\-Tabelle und die benutzerdefinierte Aktion In\-Script Execution Options.  
  
 Benutzerdefinierte Aktionen vom Typ 50 angeben die Eigenschaft, die die ausführbare Datei als Wert für die Quellspalte und die Befehlszeilenargumente in der Zielspalte.  
  
### CustomAction Tabellenzeilen devenv.exe ausgeführt.  
  
|Aktion|Typ|Quelle|Ziel|  
|------------|---------|------------|----------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/ Setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/ Setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/ Setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/ Setup|  
  
 Benutzerdefinierte Aktionen müssen in der Tabelle InstallExecuteSequence Planung für die Ausführung bei der Installation erstellt werden. Verwenden Sie die entsprechende Eigenschaft in jeder Zeile der Spalte Bedingung zu verhindern, dass die benutzerdefinierte Aktion ausgeführt werden, wenn diese Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht auf dem System installiert ist.  
  
> [!NOTE]
>  `Null` Auswerten von Eigenschaften zu `False` beim bedingt verwendet.  
  
 Der Wert des Sequence\-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequence\-Werte in der Windows Installer\-Paket. Sequenz\-Schlüsselwerte sein, daß devenv.exe benutzerdefinierten Aktionen ausführen als möglichst unmittelbar vor der Standardaktion InstallFinalize schließen.  
  
### Tabelle InstallExecuteSequence devenv.exe benutzerdefinierten Aktionen zu planen.  
  
|Aktion|Bedingung|Sequenz|  
|------------|---------------|-------------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)