---
title: CreatePkgDef-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63334ba9d454407bb93a87bf89b12cb472184d58
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181596"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine DLL-Datei für Visual Studio-Erweiterung als Parameter akzeptiert, und erstellt eine PKGDEF-Datei, um die DLL-Datei zu begleiten. Die PKGDEF-Datei enthält alle Informationen, die in die systemregistrierung andernfalls geschrieben werden sollen, wenn die Erweiterung installiert ist.  
  
> [!NOTE]
>  Die meisten der Projektvorlagen, die in Visual Studio SDK, automatisch enthalten sind erstellen PKGDEF-Dateien als Teil des Buildprozesses. Dieses Dokument richtet sich für diejenigen, die Pakete manuell erstellen, oder konvertieren Sie vorhandene Pakete, um die PKGDEF-Bereitstellung verwenden möchten.  
  
## <a name="syntax"></a>Syntax  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumente  
 / out =`FileName`  
 Erforderlich. Legt den Namen der Ausgabedatei um PKGDEF fest`FileName`.  
  
 /codebase  
 Dies ist optional. Erzwingt, dass die Registrierung mit dem Hilfsprogramm für die Codebasis.  
  
 / Assembly  
 Erzwingt, dass die Registrierung mit dem Hilfsprogramm für die Assembly.  
  
 `AssemblyPath`  
 Der Pfad der DLL-Datei aus der Sie der PKGDEF generieren möchten.  
  
## <a name="remarks"></a>Hinweise  
 Bereitstellung von Erweiterungen mithilfe der PKGDEF-Dateien ersetzt, die Anforderungen der Registrierung von früheren Versionen von Visual Studio.  
  
 Die PKGDEF-Dateien müssen in einem der folgenden Speicherorte installiert sein: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ oder %vsinstalldir%\Common7\IDE\Extensions\\. Ist der Installationsordner %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, die Erweiterung wird von Visual Studio erkannt, aber standardmäßig deaktiviert sein. Der Benutzer kann mit die Erweiterung aktivieren **Erweiterungen und Updates**. Ist der Installationsordner %vsinstalldir%\Common7\IDE\Extensions\\, die Erweiterung ist standardmäßig aktiviert.  
  
> [!NOTE]
>  Die **Erweiterungen und Updates** Tool kann nicht verwendet werden, um eine Erweiterung zugreifen, es sei denn, es als Teil eines VSIX-Pakets installiert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [CreateExpInstance-Hilfsprogramm](../../extensibility/internals/createexpinstance-utility.md)

