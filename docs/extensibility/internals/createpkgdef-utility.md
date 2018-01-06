---
title: CreatePkgDef Hilfsprogramm | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47316f6bd47d5d528dc6e36dfe3a4bcb67e00909
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="createpkgdef-utility"></a>CreatePkgDef-Hilfsprogramm
Eine DLL-Datei für eine Visual Studio-Erweiterung als Parameter akzeptiert, und erstellt eine PKGDEF-Datei, um die DLL-Datei zu begleiten. Die PKGDEF-Datei enthält alle Informationen, die in der systemregistrierung andernfalls geschrieben werden würde, wenn die Erweiterung installiert ist.  
  
> [!NOTE]
>  Die meisten der Projektvorlagen, die in Visual Studio SDK, automatisch enthalten sind erstellen PKGDEF-Dateien als Teil des Buildprozesses. Dieses Dokument ist für Benutzer gedacht, die Pakete manuell erstellen, oder konvertieren Sie vorhandene Pakete, damit PKGDEF-Bereitstellung verwenden möchten.  
  
## <a name="syntax"></a>Syntax  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumente  
 / out =`FileName`  
 Erforderlich. Legt den Namen der Ausgabedatei um PKGDEF`FileName`.  
  
 /codebase  
 Dies ist optional. Erzwingt, dass die Registrierung mit dem CodeBase-Hilfsprogramm.  
  
 / Assembly  
 Erzwingt, dass die Registrierung mit dem Dienstprogramm Assembly.  
  
 `AssemblyPath`  
 Der Pfad der DLL-Datei, die von der Sie die PKGDEF generieren möchten.  
  
## <a name="remarks"></a>Hinweise  
 Erweiterung Bereitstellung mithilfe von PKGDEF Dateien ersetzt die Registrierung-Anforderungen von früheren Versionen von Visual Studio.  
  
 Die PKGDEF-Dateien müssen in einem der folgenden Speicherorte installiert sein: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ oder %vsinstalldir%\Common7\IDE\Extensions\\. Wenn Sie der Installationsordner %localappdata%\Microsoft\Visual Studio\14.0\Extensions ist\\, die Erweiterung wird von Visual Studio erkannt werden, aber standardmäßig deaktiviert. Der Benutzer kann mit die Erweiterung aktivieren **Erweiterungen und Updates**. Wenn der Ordner "Installation" %vsinstalldir%\Common7\IDE\Extensions ist\\, die Erweiterung ist standardmäßig aktiviert.  
  
> [!NOTE]
>  Die **Erweiterungen und Updates** Tool kann nicht verwendet werden, um eine Erweiterung zugreifen, es sei denn, es als Teil eines VSIX-Pakets installiert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [CreateExpInstance-Hilfsprogramm](../../extensibility/internals/createexpinstance-utility.md)