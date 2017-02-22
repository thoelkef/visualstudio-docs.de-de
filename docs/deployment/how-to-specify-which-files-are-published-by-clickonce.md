---
title: "How to: Specify Which Files Are Published by ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, file exclusion"
  - "files, publishing via ClickOnce"
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify Which Files Are Published by ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung werden alle Dateien im Projekt, die keine Codedateien sind, zusammen mit der Anwendung bereitgestellt.  In einigen Fällen möchten oder müssen Sie bestimmte Dateien nicht veröffentlichen, oder Sie möchten bestimmte Dateien anhand von Bedingungen installieren.  Mit Visual Studio können Dateien ausgeschlossen oder als erforderliche Komponenten bzw. Datendateien markiert werden. Außerdem lassen sich Dateigruppen für die bedingte Installation erstellen.  
  
 Dateien für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung werden im **Projekt\-Designer** auf der Seite **Veröffentlichen** mithilfe des Dialogfelds **Anwendungsdateien** verwaltet.  
  
 Zunächst ist eine einzelne Dateigruppe mit dem Namen **\(Erforderlich\)** vorhanden.  Sie können weitere Dateigruppen erstellen und ihnen Dateien zuweisen.  Die **Downloadgruppe** kann nicht für für Dateien geändert werden, die für die Ausführung der Anwendung erforderlich sind.  Zum Beispiel müssen die EXE\-Datei der Anwendung oder als Datendateien markierte Dateien zu der Gruppe **\(Required\)** gehören.  
  
 Der Standardwert des Veröffentlichungsstatus einer Datei wird mit **\(Auto\)** markiert.  Die EXE\-Datei der Anwendung verfügt z. B. in der Standardeinstellung über den Veröffentlichungsstatus **Einschließen \(Auto\)**.  
  
 Dateien, für die die **Build Action**\-Eigenschaft auf **Inhalt** festgelegt ist, werden als Anwendungsdateien bezeichnet und standardmäßig als "Eingeschlossen" markiert.  Sie können den Status "Eingeschlossen" oder "Ausgeschlossen" haben oder als Datendateien markiert sein.  Dabei gelten folgende Ausnahmen:  
  
-   Datendateien wie SQL Database \(.mdf und .mdb\)\- und XML\-Dateien werden standardmäßig als Datendateien markiert.  
  
-   Verweise auf Assemblys \(DLL\-Dateien\) werden beim Hinzufügen des Verweises wie folgt gekennzeichnet: Wenn **Lokale Kopie** auf **False** festgelegt ist, wird sie standardmäßig als erforderliche Assembly \(**Erforderliche Komponente \(Auto\)**\) markiert, die im GAC vorhanden sein muss, bevor die Anwendung installiert wird.  Wenn **Lokale Kopie** auf **True** festgelegt ist, wird die Assembly standardmäßig als Anwendungsassembly \(**Einschließen \(Auto\)**\) markiert und bei der Installation in den Anwendungsordner kopiert.  Ein COM\-Verweis wird nur dann im Dialogfeld **Anwendungsdateien** \(als OCX\-Datei\) angezeigt, wenn dessen **Isolated**\-Eigenschaft auf **True** festgelegt ist.  Standardmäßig ist er eingeschlossen.  
  
### So fügen Sie dem Dialogfeld "Anwendungsdateien" Dateien hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** eine Datei aus.  
  
2.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Build Action** auf den Wert **Inhalt** fest.  
  
### So schließen Sie Dateien von der ClickOnce\-Veröffentlichung aus  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Anwendungsdateien**, um das Dialogfeld **Anwendungsdateien** zu öffnen.  
  
4.  Wählen Sie im Dialogfeld **Anwendungsdateien** die Datei aus, die Sie ausschließen möchten.  
  
5.  Wählen Sie im Feld **Veröffentlichungsstatus** in der Dropdownliste die Option **Ausschließen** aus.  
  
### So markieren Sie Dateien als Datendateien  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Anwendungsdateien**, um das Dialogfeld **Anwendungsdateien** zu öffnen.  
  
4.  Wählen Sie im Dialogfeld **Anwendungsdateien** die Datei aus, die Sie als Daten markieren möchten.  
  
5.  Wählen Sie im Feld **Veröffentlichungsstatus** in der Dropdownliste die Option **Datendatei** aus.  
  
### So markieren Sie Dateien als erforderliche Komponenten  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Anwendungsdateien**, um das Dialogfeld **Anwendungsdateien** zu öffnen.  
  
4.  Wählen Sie im Dialogfeld **Anwendungsdateien** die Anwendungsassembly \(DLL\-Datei\) aus, die Sie als erforderliche Komponente markieren möchten.  Beachten Sie, dass Ihre Anwendung über einen Verweis auf die Anwendungsassembly verfügen muss, um in der Liste angezeigt zu werden.  
  
5.  Wählen Sie im Feld **Veröffentlichungsstatus** in der Dropdownliste die Option **Erforderliche Komponente** aus.  
  
### So fügen Sie eine neue Dateigruppe hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Anwendungsdateien**, um das Dialogfeld **Anwendungsdateien** zu öffnen.  
  
4.  Wählen Sie im Dialogfeld **Anwendungsdateien** das Feld **Gruppieren** für die Datei aus, die Sie in die neue Gruppe aufnehmen möchten.  
  
    > [!NOTE]
    >  Für Dateien muss die **Build Action**\-Eigenschaft auf **Inhalt** festgelegt werden, bevor die Dateinamen im Dialogfeld **Anwendungsdateien** angezeigt werden.  
  
5.  Wählen Sie im Feld **Downloadgruppe** in der Dropdownliste die Option **\<Neu...\>** aus.  
  
6.  Geben Sie im Dialogfeld **Neue Gruppe** einen Namen für die Gruppe ein, und klicken Sie anschließend auf **OK**.  
  
### So fügen Sie einer Gruppe eine Datei hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Anwendungsdateien**, um das Dialogfeld **Anwendungsdateien** zu öffnen.  
  
4.  Wählen Sie im Dialogfeld **Anwendungsdateien** das Feld **Gruppieren** für die Datei aus, die Sie in die neue Gruppe aufnehmen möchten.  
  
5.  Wählen Sie im Feld **Downloadgruppe** in der Dropdownliste eine Gruppe aus.  
  
    > [!NOTE]
    >  Die **Downloadgruppe** kann nicht für für Dateien geändert werden, die für die Ausführung der Anwendung erforderlich sind.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)