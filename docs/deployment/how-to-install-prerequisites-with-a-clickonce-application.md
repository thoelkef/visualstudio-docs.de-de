---
title: 'Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d803ae651d75dd6195e4046b86a77d46d3174fc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung
Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen erfordern, dass die richtige Version von .NET Framework auf einem Computer installiert ist, bevor sie ausgeführt werden können, haben zahlreiche Anwendungen sowie andere erforderliche Komponenten. Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, wählen Sie einen Satz von erforderlichen Komponenten zusammen mit der Anwendung verpackt werden. Zeitpunkt der Installation wird eine Überprüfung ausgeführt werden, für jede erforderliche Komponente, um festzustellen, ob er bereits vorhanden ist; Wenn nicht es vor der Installation installiert werden die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
 Statt Verpacken und Veröffentlichen von erforderlichen Komponenten, können Sie auch einen Downloadpfad für die Komponenten angeben. Z. B. statt einschließlich Voraussetzungen, die mit jeder Anwendung, die Sie veröffentlichen, können eine zentrale Dateifreigabe oder die Webadresse, die die Installationsprogramme für alle Ihre Komponenten enthält, zum Zeitpunkt der Installation der Komponenten heruntergeladen werden und aus diesem Speicherort installiert.  
  
> [!IMPORTANT]
>  Sollten Sie erforderliche Installer-Pakete auf Ihrem Entwicklungscomputer hinzufügen, vor dem Veröffentlichen Ihres ersten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Weitere Informationen finden Sie unter [wie: Einschließen von Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Erforderliche Komponenten werden verwaltet, der **Voraussetzungen** (Dialogfeld), aus zugegriffen werden kann die **veröffentlichen** Bereich des der **Projekt-Designer**.  
  
> [!NOTE]
>  Zusätzlich zu den vordefinierten Liste der erforderlichen Komponenten können Sie Ihren eigenen Komponenten zur Liste hinzufügen. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Voraussetzungen für die Installation mit einer ClickOnce-Anwendung angeben  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Voraussetzungen** zu öffnen die **Voraussetzungen** (Dialogfeld).  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  In der **Voraussetzungen** aus, aktivieren Sie die Komponenten, die Sie verwenden möchten, installieren, und klicken Sie dann auf **OK**.  
  
     Die ausgewählten Komponenten werden verpackt und zusammen mit Ihrer Anwendung veröffentlicht werden.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>An einen anderen Downloadpfad für erforderliche Komponenten  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Voraussetzungen** zu öffnen die **Voraussetzungen** (Dialogfeld).  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  In der **Installationsort für erforderliche Komponenten angeben** Abschnitt **erforderliche Komponenten von folgendem Speicherort herunterladen**.  
  
6.  Wählen Sie einen Speicherort aus der Dropdown-Liste, oder geben Sie eine URL, den Dateipfad oder den FTP-Speicherort, und klicken Sie dann auf **OK.**  
  
    > [!NOTE]
    >  Sie müssen sicherstellen, dass Installationsprogramme für den angegebenen Komponenten am angegebenen Speicherort vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)