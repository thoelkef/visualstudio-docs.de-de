---
title: Debuggen von ASP.NET-Anwendungen bereitgestellten | Microsoft-Dokumentation
ms.date: 06/30/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: f911cafb8ee0bdd341ce13c6eb38423ae4d3f473
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399389"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debuggen von ASP.NET-Anwendungen bereitgestellten
Um eine bereitgestellte und ausgeführte Anwendung über [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu debuggen, müssen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess anhängen und sicherstellen, dass der Debugger auf Symbole für die Anwendung zugreifen kann. Außerdem müssen Sie die Quelldateien für die Anwendung lokalisieren und öffnen. Weitere Informationen finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md), und [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Wenn Sie zum Anfügen der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Arbeitsprozess für das Debuggen und erreicht einen Haltepunkt, der gesamte verwaltete Code im Arbeitsprozess angehalten. Das Anhalten des gesamten verwalteten Codes im Arbeitsprozess kann zu einem Arbeitsstopp für alle Benutzer des Servers führen. Wenn Sie auf einem Produktionsserver debuggen, müssen Sie unter allen Umständen die möglichen Auswirkungen auf die Produktion beachten.

Das Anhängen an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess unterscheidet sich nicht vom Anhängen an einen beliebigen anderen Remoteprozess. Wenn das passende Projekt nicht geöffnet ist, wird nach dem Anhängen ein Dialogfeld angezeigt, sobald die Anwendung unterbrochen wird. Dieses Dialogfeld fordert Sie auf, den Speicherort der Quelldateien der Anwendung anzugeben. Der im Dialogfeld eingegebene Dateiname muss mit dem Dateinamen übereinstimmen, der in den Debugsymbolen (auf dem Webserver) angegeben ist. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Zum Einrichten des Remotedebuggens auf IIS, finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Viele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen verweisen auf DLLs, die Geschäftslogik oder sonstigen nützlichen Code enthalten. Solch ein Verweis kopiert die DLL aus Ihrem lokalen Computer in den Ordner "\bin" des virtuellen Verzeichnisses der Webanwendung, wenn Sie Ihre app bereitstellen. Beim Debuggen sollten Sie beachten, dass die Webanwendung nicht auf die Kopie der DLL auf dem lokalen Computer, sondern auf diese Kopie der DLL verweist.

## <a name="see-also"></a>Siehe auch
- [Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Vorgehensweise: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)