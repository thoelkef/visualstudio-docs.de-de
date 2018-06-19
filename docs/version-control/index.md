---
layout: LandingPage
title: Versionskontrolle in Visual Studio | VSTS und TFS
description: Leitfaden für die ersten Schritte mit der Versionskontrolle in Visual Studio
keywords: VSTS, TFS, Versionskontrolle
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 428139af8680bc60f4456367d1a17d4c97874efc
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "29795351"
---
# <a name="version-control-in-visual-studio"></a>Versionskontrolle in Visual Studio

Versionskontrollsysteme ermöglichen Ihnen das Nachverfolgen von Änderungen am Code über einen bestimmten Zeitraum. Wenn Sie Änderungen vornehmen, erstellt das Versionskontrollsystem eine Momentaufnahme von Ihren Dateien. Das Versionskontrollsystem speichert die Momentaufnahme dauerhaft, sodass Sie sie bei Bedarf später abrufen können. Visual Studio stellt [Git](/vsts/git/index) und die [TFVC (Team Foundation Version Control, Team Foundation-Versionskontrolle)](/vsts/tfvc/index) bereit. Informationen, die Ihnen die Wahl zwischen den beiden Systemen erleichtern, finden Sie unter [Auswählen der richtigen Versionskontrolle für das Projekt](/vsts/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git
Git ist aktuell das am häufigsten verwendete Versionskontrollsystem und hat sich schnell als Standard für die Versionskontrolle etabliert. Git ist ein verteiltes Versionskontrollsystem. Dies bedeutet, dass Ihre lokale Kopie des Codes ein vollständiges Versionskontrollrepository darstellt. Diese voll funktionsfähigen lokalen Repositorys erleichtern das Offline- oder Remotearbeiten. Sie committen Ihre Arbeit lokal und synchronisieren dann Ihre Kopie des Repositorys mit der Kopie auf dem Server. Dieses Paradigma unterscheidet sich von der zentralisierten Versionskontrolle, bei der Clients Code mit einem Server synchronisieren müssen, bevor neue Versionen des Codes erstellt werden.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://www.visualstudio.com/learn-git/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Informationen zu Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Erste Schritte mit Git mit Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/tutorial/clone?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Klonen eines vorhandenen Git-Repositorys</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Team Foundation-Versionskontrolle (TFVC) ist ein zentralisiertes Quellcodeverwaltungssystem. In der Regel verfügen Teammitglieder auf ihren Entwicklungscomputern nur über eine Version jeder Datei. Daten zur Versionsgeschichte einer Datei werden nur auf dem Server gespeichert. Verzweigungen sind pfadbasiert und werden auf dem Server erstellt.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/vsts/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Informationen zur TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Erste Schritte mit der TFVC in Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/vsts/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Überprüfen Ihres Codes</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Ressourcen 

- [Pro Git (Buch)](https://git-scm.com/book/en/v2)  
- [Planen Ihrer Migration nach Git](https://www.visualstudio.com/learn/centralized-to-git/)  
- [Migrieren von der TFVC nach Git](https://www.visualstudio.com/learn/migrate-from-tfvc-to-git/)  

 

