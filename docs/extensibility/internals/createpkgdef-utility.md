---
title: "CreatePkgDef-Dienstprogramm | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Paketdefinition"
  - "Erstellen Sie die pkgdef"
  - "PKGDEF"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CreatePkgDef-Dienstprogramm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine DLL\-Datei für Visual Studio\-Erweiterung als Parameter akzeptiert, und erstellt eine PKGDEF\-Datei, um die DLL\-Datei zu begleiten. Die PKGDEF\-Datei enthält alle Informationen, die in der Registrierung andernfalls geschrieben werden würde, wenn die Erweiterung installiert ist.  
  
> [!NOTE]
>  Die meisten der Projektvorlagen, die in Visual Studio SDK, automatisch enthalten sind erstellen PKGDEF\-Dateien als Teil des Buildprozesses. Dieses Dokument richtet für diejenigen, die Pakete manuell erstellen, oder konvertieren vorhandene Pakete, um die PKGDEF\-Bereitstellung verwenden möchten.  
  
## Syntax  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## Argumente  
 \/ out \=`FileName`  
 Erforderlich. Legt den Namen der Ausgabedatei PKGDEF auf```FileName`.  
  
 \/codebase  
 Optional. Erzwingt die Registrierung mit dem CodeBase\-Hilfsprogramm.  
  
 \/ Assembly  
 Erzwingt die Registrierung mit dem Dienstprogramm für die Assembly.  
  
 `AssemblyPath`  
 Der Pfad der DLL\-Datei aus der Sie die PKGDEF generieren möchten.  
  
## Hinweise  
 Bereitstellen der Erweiterung mithilfe der PKGDEF\-Dateien ersetzt, die Registrierung Anforderungen von früheren Versionen von Visual Studio.  
  
 Die PKGDEF\-Dateien müssen in einem der folgenden Speicherorte installiert werden: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ oder % vsinstalldir%\\Common7\\IDE\\Extensions\\. Ist der Ordner %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\, wird die Erweiterung wird von Visual Studio erkannt, aber standardmäßig deaktiviert. Der Benutzer kann mit die Erweiterung aktivieren **Erweiterungen und Updates**. Wenn der Ordner % vsinstalldir%\\Common7\\IDE\\Extensions\\ ist, wird die Erweiterung standardmäßig aktiviert.  
  
> [!NOTE]
>  Die **Erweiterungen und Updates** Tool kann nicht verwendet werden, um eine Erweiterung zugreifen, wenn es als Teil eines VSIX\-Pakets installiert ist.  
  
## Siehe auch  
 [CreateExpInstance\-Dienstprogramm](../../extensibility/internals/createexpinstance-utility.md)