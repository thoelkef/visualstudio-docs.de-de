---
title: Reservierte und bekannte Eigenschaften für MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181081"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Reservierte und bekannte Eigenschaften für MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] stellt eine Reihe vordefinierter Eigenschaften zum Speichern von Informationen über die Projektdatei und die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Binärdateien bereit. Diese Eigenschaften werden auf dieselbe Weise ausgewertet wie andere [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Eigenschaften. Zum Verwenden der `MSBuildProjectFile`-Eigenschaft geben Sie beispielsweise `$(MSBuildProjectFile)` ein.  
  
 MSBuild verwendet die Werte in der folgenden Tabelle, um die reservierten und bekannten Eigenschaften vorzudefinieren. Reservierte Eigenschaften können nicht überschrieben werden, aber bekannte Eigenschaften können überschrieben werden, indem identisch benannte Umgebungseigenschaften, globale Eigenschaften oder Eigenschaften verwendet werden, die in der Projektdatei deklariert sind.  
  
## <a name="reserved-and-well-known-properties"></a>Reservierte und bekannte Eigenschaften  
 In der folgenden Tabelle werden die vordefinierten [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Eigenschaften beschrieben.  
  
|Eigenschaft|BESCHREIBUNG|Reserviert oder bekannt|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Der absolute Pfad des Ordners, in dem sich die zurzeit verwendeten [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Binärdateien befinden (z.B. C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Diese Eigenschaft ist nützlich, wenn Sie auf Dateien im [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Verzeichnis verweisen müssen.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Reserviert|  
|`MSBuildExtensionsPath`|Seit .NET Framework 4 gibt es keinen Unterschied zwischen den Standardwerten von `MSBuildExtensionsPath` und `MSBuildExtensionsPath32`. Sie können die Umgebungsvariable `MSBUILDLEGACYEXTENSIONSPATH` auf einen Wert ungleich NULL festlegen, um das Verhalten des Standardwerts von `MSBuildExtensionsPath` in früheren Versionen zu ermöglichen.<br /><br /> In .NET Framework 3.5 und Vorgängerversionen verweist der Standardwert von `MSBuildExtensionsPath` auf den Pfad des MSBuild-Unterordners unter dem Ordner "\Program Files\" oder "\Program Files (x86)", je nach Bitanzahl des aktuellen Prozesses. Bei einem 32-Bit-Prozess auf einem 64-Bit-Computer zeigt diese Eigenschaft beispielsweise auf den Ordner "\Programme (x86)". Bei einem 64-Bit-Prozess auf einem 64-Bit-Computer zeigt diese Eigenschaft auf den Ordner "\Programme".<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.<br /><br /> Dieser Speicherort ist nützlich zum Ablegen benutzerdefinierter Zieldateien. Ihre Zieldateien können beispielsweise unter "\Programme\MSBuild\MyFiles\Northwind.targets" installiert sein und dann mithilfe des folgenden XML-Codes in Projektdateien importiert werden:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Bekannt|  
|`MSBuildExtensionsPath32`|Der Pfad zu dem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Unterordner unter dem Ordner "\Programme" oder "\Programme (x86)". Dieser Pfad zeigt stets auf den 32-Bit-Ordner "\Programme" auf einem 32-Bit-Computer und auf "\Programme (x86)" auf einem 64-Bit-Computer. Siehe auch `MSBuildExtensionsPath` und `MSBuildExtensionsPath64`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Bekannt|  
`MSBuildExtensionsPath64`|Der Pfad des [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Unterordners im Ordner „\Programme“. Bei einem 64-Bit-Computer zeigt dieser Pfad immer auf den Ordner "\Programme". Bei einem 32-Bit-Computer ist dieser Pfad leer. Siehe auch `MSBuildExtensionsPath` und `MSBuildExtensionsPath32`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Bekannt|  
|`MSBuildLastTaskResult`|`true`, wenn die vorherige Aufgabe ohne Fehler (auch wenn Warnungen auftraten) abgeschlossen wurde, oder `false`, wenn bei der vorherigen Aufgabe Fehler aufgetreten sind. Wenn ein Fehler in einer Aufgabe auftritt, ist das Auftreten des Fehlers in der Regel das letzte Ereignis in dem jeweiligen Projekt. Daher ist der Wert dieser Eigenschaft niemals `false`, außer in diesen Szenarien:<br /><br /> - wenn für das `ContinueOnError`-Attribut des [Task Element (MSBuild) (Aufgabenelement (MSBuild))](../msbuild/task-element-msbuild.md) `WarnAndContinue` (oder `true`) bzw. `ErrorAndContinue` festgelegt wird.<br /><br /> - wenn `Target` über ein [OnError Element (MSBuild) (OnError-Element (MSBuild))](../msbuild/onerror-element-msbuild.md) als untergeordnetes Element verfügt.|Reserviert|  
|`MSBuildNodeCount`|Die maximale Anzahl nebenläufiger Prozesse, die beim Erstellen verwendet werden. Dies ist der Wert, den Sie in der Befehlszeile für **/maxcpucount** angegeben haben. Wenn Sie **/maxcpucount** ohne einen Wert angegeben haben, wird die Anzahl der Prozessoren im Computer durch `MSBuildNodeCount` angegeben. Weitere Informationen finden Sie unter [Command-Line Reference (Befehlszeilenreferenz)](../msbuild/msbuild-command-line-reference.md) sowie unter [Building Multiple Projects in Parallel (Gleichzeitiges Erstellen mehrerer Projekte)](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Reserviert|  
|`MSBuildProgramFiles32`|Der Speicherort des Ordners für 32-Bit-Programme, beispielsweise `C:\Program Files (x86)`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Reserviert|  
|`MSBuildProjectDefaultTargets`|Die vollständige Liste der Ziele, die im `DefaultTargets`-Attribut des `Project`-Elements angegeben sind. Das folgende `Project`-Element würde beispielsweise über einen `MSBuildDefaultTargets`-Eigenschaftswert von `A;B;C` verfügen:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Reserviert|  
|`MSBuildProjectDirectory`|Der absolute Pfad des Verzeichnisses, in dem sich die Projektdatei befindet, beispielsweise `C:\MyCompany\MyProduct`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Reserviert|  
|`MSBuildProjectDirectoryNoRoot`|Der Wert der `MSBuildProjectDirectory`-Eigenschaft, ausschließlich des Stammlaufwerks.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Reserviert|  
|`MSBuildProjectExtension`|Die Dateinamenerweiterung der Projektdatei, einschließlich des Punkts, z. B. ".proj".|Reserviert|  
|`MSBuildProjectFile`|Der vollständige Dateiname der Projektdatei, einschließlich der Dateinamenerweiterung, z. B. "MyApp.proj".|Reserviert|  
|`MSBuildProjectFullPath`|Der absolute Pfad und der vollständige Dateiname der Projektdatei, einschließlich der Dateinamenerweiterung, beispielsweise "C:\MyCompany\MyProduct\MyApp.proj".|Reserviert|  
|`MSBuildProjectName`|Der Dateiname der Projektdatei ohne die Dateinamenerweiterung, z. B. "MyApp".|Reserviert|  
|`MSBuildStartupDirectory`|Der absolute Pfad des Ordners, in dem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aufgerufen wird. Wenn Sie diese Eigenschaft verwenden, können Sie alles unterhalb eines bestimmten Punkts in einer Projektstruktur erstellen, ohne "dirs.proj"-Dateien in jedem Verzeichnis zu erstellen. Stattdessen haben Sie wie hier gezeigt nur ein Projekt, beispielsweise "C:\traversal.proj":<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Geben Sie für die Erstellung an einem beliebigen Punkt in der Struktur Folgendes ein:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.|Reserviert|  
|`MSBuildThisFile`|Der Teil von `MSBuildThisFileFullPath`, der den Dateinamen und die Dateierweiterung angibt.|Reserviert|  
|`MSBuildThisFileDirectory`|Der Teil von `MSBuildThisFileFullPath`, der das Verzeichnis angibt.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich in den Pfad ein.|Reserviert|  
|`MSBuildThisFileDirectoryNoRoot`|Der Teil von `MSBuildThisFileFullPath`, der das Verzeichnis angibt, ausschließlich des Stammlaufwerks.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich in den Pfad ein.|Reserviert|  
|`MSBuildThisFileExtension`|Der Teil von `MSBuildThisFileFullPath`, der die Dateinamenerweiterung angibt.|Reserviert|  
|`MSBuildThisFileFullPath`|Der absolute Pfad des Projekts oder der TARGETS-Datei, die das gerade ausgeführte Ziel enthält.<br /><br /> Hinweis: Sie können einen relativen Pfad in einer TARGETS-Datei angegeben, der relativ zur TARGETS-Datei und nicht relativ zur ursprünglichen Projektdatei ist.|Reserviert|  
|`MSBuildThisFileName`|Der Teil von `MSBuildThisFileFullPath`, der den Dateinamen angibt, jedoch ohne die Dateinamenerweiterung.|Reserviert|  
|`MSBuildToolsPath`|Der Installationspfad der [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Version, die mit dem Wert von `MSBuildToolsVersion` verknüpft ist.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich nicht in den Pfad ein.<br /><br /> Diese Eigenschaft kann nicht überschrieben werden.|Reserviert|  
|`MSBuildToolsVersion`|Die Version des [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Toolsets, das zum Erstellen des Projekts verwendet wird.<br /><br /> Hinweis: Ein [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Toolset besteht aus Aufgaben, Zielen und Tools, die zum Erstellen einer Anwendung verwendet werden. Zu den Tools zählen Compiler wie "csc.exe" und "vbc.exe". Weitere Informationen finden Sie unter [Toolset (ToolsVersion) (Toolset (ToolsVersion))](../msbuild/msbuild-toolset-toolsversion.md) sowie unter [Standard and Custom Toolset Configurations (Standardmäßige und benutzerdefinierte Toolsetkonfigurationen)](../msbuild/standard-and-custom-toolset-configurations.md).|Reserviert|  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md) [MSBuild-Eigenschaften](msbuild-properties1.md)
