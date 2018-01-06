---
title: CreateExpInstance-Dienstprogramm | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c1104ebfbd066ad438262fcca0186acfb3854dbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="createexpinstance-utility"></a>CreateExpInstance-Hilfsprogramm
Verwenden Sie CreateExpInstance-Hilfsprogramm um zu erstellen, wiederherstellen, oder löschen Sie eine experimentelle Instanz von Visual Studio. Sie können die experimentelle Instanz, Debuggen und Testen von Visual Studio-Erweiterungen ohne Änderung der zugrunde liegenden Produkt verwenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parameter  
 / Erstellen  
 Erstellt die experimentelle Instanz.  
  
 / Reset  
 Löscht die experimentelle Instanz, und klicken Sie dann ein neues Zertifikat erstellt.  
  
 /Clean  
 Löscht die experimentelle Instanz.  
  
 / VSInstance  
 Der Name des Verzeichnisses, das die zu kopierende Basis Visual Studio-Instanz enthält.  
  
 / RootSuffix  
 Das Suffix, um den Namen des Verzeichnisses der experimentellen Instanz angefügt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie an einer Visual Studio-Erweiterung arbeiten, drücken Sie F5, um die standardmäßige experimentelle Instanz öffnen und die aktuelle Erweiterung installieren. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio eine, die die Standardeinstellungen hat.  
  
 Der Standardspeicherort der experimentellen Instanz hängt von der Visual Studio-Versionsnummer ab. Beispielsweise ist der Speicherort für Visual Studio 2015 %localappdata%\Microsoft\VisualStudio\14.0Exp\ alle Dateien im Verzeichnis als Teil dieser Instanz. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen werden, es sei denn, der Verzeichnisname am Standardspeicherort geändert wird.  
  
 Visual Studio greift die systemregistrierung nicht, wenn sie die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine experimentelle Version der Registrierungsstruktur verwendet.  
  
 Das Hilfsprogramm CreateExpInstance ersetzt das Dienstprogramm VsRegEx.  
  
 Im folgende Beispiel wird die standardmäßige experimentellen Instanz von Visual Studio zurückgesetzt.  
  
 **CreateExpInstance.exe/Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../../extensibility/internals/vspackages.md)