---
title: "SignFile Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#SignFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, SignFile task"
  - "SignFile task [MSBuild]"
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# SignFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Signiert die angegebene Datei mit dem angegebenen Zertifikat.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `SignFile`\-Aufgabe beschrieben.  
  
 Beachten Sie, dass SHA\-256\-Zertifikate nur auf Computern zulässig sind, auf denen .NET 4.5 und höher installiert ist.  
  
> [!WARNING]
>  Ab Visual Studio 2013 Update 3 hat diese Aufgabe eine neue Signatur, mit der Sie die Zielframeworkversion für die Datei angeben können.  Sie sollen die neue Signatur verwenden, wo immer möglich, weil der MSBuild\-Prozess SHA\-256\-Hashes nur dann verwendet, wenn das Zielframework .NET 4.5 oder höher ist.  Wenn das Zielframework .NET 4.0 oder älter ist, wird der SHA\-256\-Hash nicht verwendet.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`CertificateThumbprint`|Erforderlicher `String`\-Parameter.<br /><br /> Gibt das zum Signieren zu verwendende Zertifikat an.  Dieses Zertifikat muss sich im persönlichen Speicher des aktuellen Benutzers befinden.|  
|`SigningTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die Dateien an, die mit dem Zertifikat signiert werden sollen.|  
|`TimestampUrl`|Optionaler `String`\-Parameter.<br /><br /> Gibt die URL eines Zeitstempelservers an.|  
|`TargetFrameworkVersion`|Die Version des .NET Framework, die für das Ziel verwendet wird.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>\-Klasse.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Task Base Class](../msbuild/task-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `SignFile`\-Aufgabe zum Signieren der Dateien verwendet, die in der `FilesToSign`\-Elementauflistung mit dem in der `Certificate`\-Eigenschaft angegebenen Zertifikat angegeben werden.  
  
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
>  Der Zertifikatfingerabdruck ist der SHA1\-Hash des Zertifikats.  Weitere Informationen finden Sie unter [Abrufen des SHA\-1\-Hashs eines vertrauenswürdigen Stammzertifizierungsstellenzertifikats](http://msdn.microsoft.com/de-de/dd641990-9a88-4228-a245-017797131a87).  
  
## Beispiel  
 Im folgenden Beispiel wird die `Exec`\-Aufgabe zum Signieren der Dateien verwendet, die in der `FilesToSign`\-Elementauflistung mit dem in der `Certificate`\-Eigenschaft angegebenen Zertifikat angegeben werden.  Damit können Sie Windows Installer\-Dateien während des Buildprozesses signieren.  
  
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
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)