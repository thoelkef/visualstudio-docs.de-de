---
title: 'Vorgehensweise: Erstellen von Konsolen Anwendungen für Zustandsautomatworkflows (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48c7e06c2cb0e59de754b1ab36b693c4c9872985
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662714"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Vorgehensweise: Erstellen von Konsolenanwendungen für Zustandsautomatworkflows (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine Konsolenanwendung für Zustandsautomatworkflows mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zu erstellen, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

### <a name="to-create-a-state-machine-application-project"></a>So erstellen Sie ein Zustandsautomatanwendungsprojekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option Visual c# oder Visual Basic (unter **andere Sprachen**) aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **Zustands Automat-Workflow Konsolenanwendung**aus.

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellen möchten, aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , und geben Sie im Feld Projektmappenname einen Namen ein. **Solution Name**

8. Klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Legacy Workflow Projekten](../workflow-designer/creating-legacy-workflow-projects.md) Gewusst [wie: Erstellen einer Zustands Automat-Workflow Bibliothek (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)