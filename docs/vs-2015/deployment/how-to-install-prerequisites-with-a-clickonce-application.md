---
title: 'Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a3619e911ffcf730012ee26d26783b6a7596704
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959536"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen erfordern, dass die richtige Version von .NET Framework auf einem Computer installiert ist, bevor sie ausgeführt werden können; viele Anwendungen verfügen über sowie andere erforderliche Komponenten. Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung können Sie eine Reihe von Komponenten, die für die zusammen mit der Anwendung verpackt werden. Bei der Installation wird eine Überprüfung ausgeführt werden, für jede erforderliche Komponente, um festzustellen, ob sie bereits vorhanden ist; Wenn nicht es vor der Installation von installiert die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
 Anstatt Verpacken und veröffentlichen die Voraussetzungen, können Sie auch einen Downloadspeicherort für die Komponenten angeben. Z. B. statt, einschließlich Voraussetzungen, die mit jeder Anwendung, die Sie veröffentlichen, können einer zentralen Dateifreigabe oder die Webadresse an, die die Installationsprogramme für alle Ihre Komponenten enthält, bei der Installation werden die Komponenten heruntergeladen und aus diesem Speicherort installiert.  
  
> [!IMPORTANT]
>  Sie sollten auf Ihrem Entwicklungscomputer erforderliche Installer-Pakete hinzufügen, vor dem Veröffentlichen Ihrer ersten [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung. Weitere Informationen finden Sie unter [Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Erforderliche Komponenten werden verwaltet die **Voraussetzungen** klicken Sie im Dialogfeld aus zugegriffen werden kann die **veröffentlichen** im Bereich der **Projekt-Designer**.  
  
> [!NOTE]
>  Zusätzlich zu den vordefinierten Liste der Voraussetzungen können Sie eigene Komponenten zur Liste hinzufügen. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Voraussetzungen für die Installation mit einer ClickOnce-Anwendung angeben  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Voraussetzungen** die Schaltfläche, um die **Voraussetzungen** Dialogfeld.  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  In der **Voraussetzungen** aus, aktivieren Sie die Komponenten, die Sie verwenden möchten, installieren, und klicken Sie dann auf **OK**.  
  
     Die ausgewählten Komponenten werden verpackt und zusammen mit Ihrer Anwendung veröffentlicht werden.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>An einen anderen Downloadpfad für erforderliche Komponenten  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Voraussetzungen** die Schaltfläche, um die **Voraussetzungen** Dialogfeld.  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  In der **Geben Sie den Installationsort für erforderliche Komponenten** wählen Sie im Abschnitt **erforderliche Komponenten von folgendem Speicherort herunterladen**.  
  
6.  Wählen Sie einen Speicherort aus der Dropdown-Liste, oder geben Sie eine URL, Dateipfad oder FTP-Speicherort, und klicken Sie dann auf **OK.**  
  
    > [!NOTE]
    >  Sie müssen sicherstellen, Installationsprogramme für den angegebenen Komponenten am angegebenen Speicherort vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
