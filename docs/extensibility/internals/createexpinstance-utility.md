---
title: CreateExpInstance-Dienstprogramm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709243"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance-Dienstprogramm
Verwenden Sie das **Dienstprogramm CreateExpInstance,** um eine experimentelle Instanz von Visual Studio zu erstellen, zurückzusetzen oder zu löschen. Sie können die experimentelle Instanz verwenden, um Visual Studio-Erweiterungen zu debuggen und zu testen, ohne das zugrunde liegende Produkt zu ändern.

## <a name="syntax"></a>Syntax

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parameter
 **/Erstellen** Erstellt die experimentelle Instanz.

 **/Reset** Löscht die experimentelle Instanz und erstellt dann eine neue Instanz.

 **/Sauber** Löscht die experimentelle Instanz.

 **/VSInstance** Der Name des Verzeichnisses, das die zu kopierende Visual Studio-Basisinstanz enthält.

 **/RootSuffix** Das Suffix, das an den Namen des experimentellen Instanzverzeichnisses angehängt werden soll.

## <a name="remarks"></a>Bemerkungen
 Wenn Sie an einer Visual Studio-Erweiterung arbeiten, können Sie F5 drücken, um die standardmäßige experimentelle Instanz zu öffnen und die aktuelle Erweiterung zu installieren. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio eine Instanz mit den Standardeinstellungen.

 Der Standardspeicherort der experimentellen Instanz hängt von der Visual Studio-Versionsnummer ab. Für Visual Studio 2015 lautet der Speicherort z. B. *%localappdata%-Microsoft-VisualStudio-14.0Exp\\*. Alle Dateien im Verzeichnisspeicherort werden als Teil dieser Instanz betrachtet. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen, es sei denn, der Verzeichnisname wird in den Standardspeicherort geändert.

 Visual Studio greift nicht auf die Systemregistrierung zu, wenn die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine experimentelle Version der Registrierungsstruktur verwendet haben.

 Das **Dienstprogramm CreateExpInstance** ersetzt das **Dienstprogramm VsRegEx.**

 Im folgenden Beispiel wird die standardmäßige experimentelle Instanz von Visual Studio zurückgesetzt:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../../extensibility/internals/vspackages.md)
