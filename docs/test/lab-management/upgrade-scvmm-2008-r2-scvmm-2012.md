---
title: Upgrade von SCVMM 2008 R2 auf SCVMM 2012 | Microsoft-Dokumentation
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7a50c075effd8c1bb63bd56b7fab04a7509d23e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Upgrade von SCVMM 2008 R2 auf SCVMM 2012

Lab Management für Team Foundation Server unterstützt SCVMM 2008 R2 und SCVMM 2012. Wenn Sie Team Foundation Server 2013 auf Team Foundation Server 2015 aktualisieren und planen, SCVMM 2008 R2 auf SCVMM 2012 zu aktualisieren, wird empfohlen, SCVMM 2012 zu aktualisieren, nachdem Sie das Upgrade auf Team Foundation Server 2015 ausgeführt haben. In diesem Thema wird beschrieben, wie SCVMM 2008 R2 auf SCVMM 2012 aktualisiert wird, wenn Sie Lab Management in Team Foundation Server 2015 verwenden.
Lab Management unterstützt SCVMM 2016 **nicht**. 

**Wichtig**: Wenn Sie SCVMM aktualisieren, führen bestimmte Schritte zu Ausfallzeiten für Team Foundation Server. Diese Schritte finden Sie unten.

## <a name="upgrading-to-scvmm-2012"></a>Upgrade auf SCVMM 2012

1. Verwenden Sie das SCVMM 2012-Installationsprogramm, um SCVMM 2008 R2-Server auf SCVMM 2012-Server zu aktualisieren.

1. Aktualisieren Sie die SCVMM-Agents auf den Hosts und Bibliotheksfreigaben.

1. Verwenden Sie die SCVMM-Administratorkonsole, um sicherzustellen, dass alle SCVMM-Komponenten funktionieren.

1. Installieren Sie die SCVMM 2012-Administratorkonsole auf allen Computern der Team Foundation Server-Logikschicht.

1. Verwenden Sie den Befehl **iisreset**, um den Team Foundation Server-Webdienst neu zu starten. Starten Sie dann den Auftrags-Agent für Team Foundation Server neu.

   **Achtung**: Mit diesem Schritt werden die Dienste auf dem Team Foundation Server unterbrochen.

1. Aktualisieren Sie die Daten und die Vorlagen in jeder Projektauflistungsdatenbank, sodass diese mit SCVMM 2012 kompatibel sind. 
   2012.

   Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten auf dem Team Foundation Server, und geben Sie den folgenden Befehl ein:

   **C:\\Programme\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Wenn Sie den Befehl **upgradeSCVMM** verwenden, erstellt Team Foundation Server auf dem SCVMM-Server ein neues Vorlagenobjekt für jedes Teamprojekt, das diese Vorlage verwendet. Dadurch wird sichergestellt, dass die Vorlagen ohne Datenverlust aktualisiert werden, um mit SCVMM 2012 kompatibel zu sein. Wenn die neuen Vorlagen erstellt werden, wird der Teamprojektname dem Vorlagennamen angefügt.

   **Vorsicht**:  
   Wenn der neue Vorlagenname mehr als 64 Zeichen umfasst, tritt ein SCVMM-Fehler auf. Um diesen Fehler zu beheben, müssen Sie den Vorlagen einen kürzeren Namen geben. Wenn beim Ausführen dieses Befehls andere Fehler oder Warnungen auftreten, lesen Sie den nächsten Abschnitt. Dieser enthält Informationen zur Behebung dieser Fehler. Wenn keine Fehler und Warnungen auftreten, ist das Upgrade abgeschlossen und Sie können SCVMM-Umgebungen mit Lab Management verwenden.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Beheben von Fehlern und Warnungen bei Verwendung des Befehls "upgradeSCVMM"

Nachdem Sie den Befehl **upgradeSCVMM** verwendet haben, müssen Sie alle aufgetretenen Fehler oder Warnungen beheben und dann den Befehl erneut ausführen, bevor Sie Lab Management verwenden können. Der Befehl **upgradeSCVMM** generiert eine Protokolldatei, die Informationen zu aufgetretenen Fehlern und Warnungen enthält. Der Speicherort der Protokolldatei wird angezeigt, wenn Sie den Befehl **upgradeSCVMM** ausführen.

**SCVMM-Fehler**: Wenn ein Fehler auftritt, der mit einem SCVMM-Fehler verbunden ist, verwenden Sie den SCVMM-Auftragsverlauf, um weitere Informationen zum Fehler abzurufen. Nachdem Sie den Fehler in SCVMM behoben haben, führen Sie den Befehl **upgradeSCVMM** erneut aus.

## <a name="see-also"></a>Siehe auch

* [Ändern vorhandener Lab Management-Konfigurationen](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
