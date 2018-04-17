---
title: CreateExpInstance-Dienstprogramm | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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