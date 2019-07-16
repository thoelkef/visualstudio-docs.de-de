---
title: CreateExpInstance-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196983"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

CreateExpInstance-Hilfsprogramm um zu erstellen, verwenden, die durch das Zurücksetzen oder Löschen einer experimentellen Instanz von Visual Studio. Sie können die experimentelle Instanz zum Debuggen und Testen Visual Studio-Erweiterungen, ohne die zugrunde liegenden Produkt verwenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parameter  
 / Erstellen  
 Erstellt die experimentelle Instanz.  
  
 / Reset  
 Löscht die experimentelle Instanz, und klicken Sie dann eine neue erstellt.  
  
 /Clean  
 Löscht die experimentelle Instanz.  
  
 / VSInstance  
 Der Name des Verzeichnisses, das die zu kopierende grundlegende Visual Studio-Instanz enthält.  
  
 / RootSuffix  
 Das Suffix, auf den Namen des Verzeichnisses experimentelle Instanz angefügt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Visual Studio-Erweiterung arbeiten, können Sie durch Drücken auf F5, um die standardmäßige experimentelle Instanz öffnen, und installieren Sie die aktuelle Erweiterung. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio mit einem Konto mit den Standardeinstellungen.  
  
 Der Standardspeicherort der experimentellen Instanz hängt von der Visual Studio-Versionsnummer ab. Beispielsweise ist der Speicherort für Visual Studio 2015, %localappdata%\Microsoft\VisualStudio\14.0Exp\ alle Dateien in das Verzeichnis werden als Teil dieser Instanz betrachtet. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen werden, es sei denn, der den Namen des Verzeichnisses am Standardspeicherort geändert wird.  
  
 Visual Studio greift die Registrierung des Systems nicht, wenn sie die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine experimentelle Version der Registrierungsstruktur verwendet.  
  
 Das Dienstprogramm VsRegEx, ersetzt das CreateExpInstance-Hilfsprogramm.  
  
 Im folgenden Beispiel wird die Standardwert für die experimentellen Instanz von Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance=14.0 /rootsuffix=Exp**  
  
## <a name="see-also"></a>Siehe auch  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)
