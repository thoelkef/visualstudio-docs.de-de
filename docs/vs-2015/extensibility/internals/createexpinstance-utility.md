---
title: "\"|\"-Hilfsprogramm | Microsoft-Dokumentation"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196983"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie das Hilfsprogramm "| ateexpinstance", um eine experimentelle Instanz von Visual Studio zu erstellen, zurückzusetzen oder zu löschen. Sie können die experimentelle Instanz verwenden, um Visual Studio-Erweiterungen zu Debuggen und zu testen, ohne das zugrunde liegende Produkt ändern  
  
## <a name="syntax"></a>Syntax  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parameter  
 /Create  
 Erstellt die experimentelle Instanz.  
  
 /Reset  
 Löscht die experimentelle Instanz und erstellt dann eine neue.  
  
 /Clean  
 Löscht die experimentelle Instanz.  
  
 /VSInstance  
 Der Name des Verzeichnisses, das die zu kopierenden Basis-Visual Studio-Instanz enthält.  
  
 /RootSuffix  
 Das Suffix, das an den Namen des experimentellen Instanzverzeichnisses angehängt werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie an einer Visual Studio-Erweiterung arbeiten, können Sie F5 drücken, um die standardmäßige experimentelle Instanz zu öffnen und die aktuelle Erweiterung zu installieren. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio eine mit den Standardeinstellungen.  
  
 Der Standard Speicherort der experimentellen Instanz hängt von der Versionsnummer von Visual Studio ab. Für Visual Studio 2015 lautet der Speicherort beispielsweise%LocalAppData%\microsoft\visualstudio\14.0exp\ alle Dateien im Verzeichnis Speicherort werden als Teil dieser Instanz betrachtet. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen, es sei denn, der Verzeichnisname wird in den Standard Speicherort geändert.  
  
 Visual Studio greift nicht auf die Systemregistrierung zu, wenn die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine experimentelle Version der Registrierungs Struktur verwendet haben.  
  
 Das Hilfsprogramm "| ateexpinstance" ersetzt das Hilfsprogramm "vsregex".  
  
 Im folgenden Beispiel wird die standardmäßige experimentelle Instanz von Visual Studio zurückgesetzt.  
  
 **CreateExpInstance.exe/Reset/VSInstance = 14,0/RootSuffix = Exp**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)
