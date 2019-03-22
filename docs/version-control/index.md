---
layout: LandingPage
title: Versionskontrolle
description: Leitfaden für die ersten Schritte mit der Versionskontrolle in Visual Studio
keywords: 'VSTS, TFS, Versionskontrolle'
author: steved0x
ms.manager: jillfra
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
  - multiple
---
# <a name="version-control-in-visual-studio"></a>Versionskontrolle in Visual Studio

Versionskontrollsysteme ermöglichen Ihnen das Nachverfolgen von Änderungen am Code über einen bestimmten Zeitraum. Wenn Sie Änderungen vornehmen, erstellt das Versionskontrollsystem eine Momentaufnahme von Ihren Dateien. Das Versionskontrollsystem speichert die Momentaufnahme dauerhaft, sodass Sie sie bei Bedarf später abrufen können. Visual Studio stellt [Git](/azure/devops/repos/git/index?view=vsts) und die [TFVC (Team Foundation Version Control, Team Foundation-Versionskontrolle)](/azure/devops/repos/tfvc/index?view=vsts) bereit. Informationen, die Ihnen die Wahl zwischen den beiden Systemen erleichtern, finden Sie unter [Auswählen der richtigen Versionskontrolle für das Projekt](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git

Git ist aktuell das am häufigsten verwendete Versionskontrollsystem und hat sich schnell als Standard für die Versionskontrolle etabliert. Git ist ein verteiltes Versionskontrollsystem. Dies bedeutet, dass Ihre lokale Kopie des Codes ein vollständiges Versionskontrollrepository darstellt. Diese voll funktionsfähigen lokalen Repositorys erleichtern das Offline- oder Remotearbeiten. Sie committen Ihre Arbeit lokal und synchronisieren dann Ihre Kopie des Repositorys mit der Kopie auf dem Server. Dieses Paradigma unterscheidet sich von der zentralisierten Versionskontrolle, bei der Clients Code mit einem Server synchronisieren müssen, bevor neue Versionen des Codes erstellt werden.

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
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
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Erste Schritte mit Git in Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
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
        <a href="/azure/devops/repos/tfvc/overview">
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
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
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
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
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
- [Planen Ihrer Migration nach Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migrieren von der TFVC nach Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [Versionskontrolle (Visual Studio für Mac)](/visualstudio/mac/version-control)