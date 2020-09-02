---
title: SignFile-Aufgabe| Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08db6a5d22cacc348a9ef36fd9e9857d5b55642a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703735"
---
# <a name="signfile-task"></a>SignFile-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Signiert die angegebene Datei mit dem angegebenen Zertifikat.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `SignFile` -Aufgabe beschrieben.  
  
 Beachten Sie, dass SHA-256-Zertifikate nur auf Computern zulässig sind, auf denen .NET 4.5 und höher installiert ist.  
  
> [!WARNING]
> Ab Visual Studio 2013 Update 3 hat diese Aufgabe eine neue Signatur, mit der Sie die Zielframeworkversion für die Datei angeben können. Sie sollen die neue Signatur verwenden, wo immer möglich, weil der MSBuild-Prozess SHA-256-Hashes nur dann verwendet, wenn das Zielframework .NET 4.5 oder höher ist. Wenn das Zielframework .NET 4.0 oder älter ist, wird der SHA-256-Hash nicht verwendet.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`CertificateThumbprint`|Erforderlicher `String` -Parameter.<br /><br /> Gibt das zum Signieren zu verwendende Zertifikat an. Dieses Zertifikat muss sich im persönlichen Speicher des aktuellen Benutzers befinden.|  
|`SigningTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die Dateien an, die mit dem Zertifikat signiert werden sollen.|  
|`TimestampUrl`|Optionaler `String`-Parameter.<br /><br /> Gibt die URL eines Zeitstempelservers an.|  
|`TargetFrameworkVersion`|Die Version des .NET Framework, die für das Ziel verwendet wird.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Task Base Class](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `SignFile`-Aufgabe zum Signieren der Dateien verwendet, die in der `FilesToSign`-Elementauflistung mit dem in der `Certificate`-Eigenschaft angegebenen Zertifikat angegeben werden.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
> Der Zertifikatfingerabdruck ist der SHA1-Hash des Zertifikats. Weitere Informationen finden Sie unter [Abrufen des SHA-1-Hashs eines vertrauenswürdigen Zertifikats der Stamm Zertifizierungs](https://msdn.microsoft.com/dd641990-9a88-4228-a245-017797131a87)Stelle.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `Exec`-Aufgabe zum Signieren der Dateien verwendet, die in der `FilesToSign`-Elementauflistung mit dem in der `Certificate`-Eigenschaft angegebenen Zertifikat angegeben werden. Damit können Sie Windows Installer-Dateien während des Buildprozesses signieren.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)
