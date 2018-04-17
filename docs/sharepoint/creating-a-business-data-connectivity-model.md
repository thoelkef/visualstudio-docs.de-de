---
title: Erstellen eines Business Data Connectivity-Modells | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f823c8c67750dec31c6c2b534ecc7500e20defaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-business-data-connectivity-model"></a>Erstellen eines Business Data Connectivity-Modells
  Sie können ein Business Data Connectivity (BDC)-Modell erstellen oder Anpassen ein vorhandenes BDC-Modell mithilfe von Visual Studio. Jede SharePoint-Projekt kann nur ein Modell enthalten. Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="creating-a-new-model"></a>Erstellen ein neues Modell  
 Um ein neues Modell zu erstellen, erstellen eine **Business Data Connectivity-Modell** oder zum Hinzufügen einer **Business Data Connectivity-Modell** Element zum ein **leeres SharePoint-Projekt**.  
  
> [!NOTE]  
>  Sie benötigen [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] auf Ihrem Computer installiert.  
  
 Visual Studio hinzugefügt dem Projekt einen Ordner. Dieser Ordner enthält den Namen, den Sie, für angeben die **Business Data Connectivity-Modell** Element in der **neues Element hinzufügen** (Dialogfeld). Wenn Sie ein neues erstellen **Business Data Connectivity-Modell** Visual Studio-Projekt den Namen des Ordners **BdcModel1**.  
  
 Visual Studio fügt die folgenden Dateien in den neuen Ordner:  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|Modelldefinitionsdatei|Enthält XML, das definiert, die Entitäten, Methoden, Line of Business (LOB)-Systemobjekte und anderen Metadaten, die das Modell beschreiben.<br /><br /> Ändern Sie die Metadaten in dieser Datei mit dem BDC-Designer, **BDC-Explorer**, **BDC-Methodendetails** Fenster und **Eigenschaften** Fenster.|  
|Entität Service-Codedatei|Enthält Methoden, die abgerufen werden, aktualisieren und Löschen von Instanzen der Entität Standardwert an.|  
  
 Um die Eigenschaften einer Entität zu definieren, bearbeiten Sie die Codedatei für die Entität ein. Weitere Informationen finden Sie unter [wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Fügen Sie Code zum Abrufen, aktualisieren und Löschen von Instanzen der Entität, der Entität Service-Codedatei. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Beim Kompilieren des Projekts erstellt Visual Studio eine Assembly an. Stellen Sie sicher, dass Sie keine weiteren Elemente nicht hinzufügen, um das Projekt, das die Projektassembly Code hinzu (z. B.: eine **sequenzieller Workflow** Element oder ein **Webpart** Element). Der Code für dieses Element wird nicht ausgeführt werden, wenn Sie die Lösung bereitgestellt werden, da das Lösungspaket die Assembly im globalen Assemblycache nicht kopiert.  Das Lösungspaket bereitstellt die Assembly, um nur das BDC-Datenbank in SharePoint.  
  
> [!NOTE]  
>  Visual Studio kopiert die Assembly in beide Speicherorte auf dem lokalen Computer an, wenn Sie das Debuggen des Projekts.  
  
## <a name="adding-an-existing-model"></a>Hinzufügen eines vorhandenen Modells  
 Sie können ein Modell importieren, die mit anderen Tools wie dem SharePoint-Designer erstellt wurde. Sie können auswählen, importieren Sie ein vorhandenes Modell in das Projekt in den folgenden Situationen:  
  
-   Um ein Modell anpassen, die bereits mit einer SharePoint-Serverfarm bereitgestellt wird.  
  
-   Verpacken und Bereitstellen eines vorhandenen Modells für mehrere SharePoint-Serverfarmen.  
  
 In beiden Fällen die LOB-Systemen, die im Modell, das Sie importieren definierten sind nicht betroffen und weiterhin wie erwartet funktionsfähig. Um ein SharePoint-Projekt ein vorhandenes Modell hinzuzufügen, verwenden Sie die Visual Studio **vorhandenes Element hinzufügen** (Dialogfeld). Weitere Informationen finden Sie unter [wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Sie können eine LOB-System vom Typ .NET Framework-Assembly importierten Modell hinzufügen, durch Auswahl einer Option in der **Hinzufügen von .NET Framework-Assembly LobSystem**. Dadurch können Sie benutzerdefinierten Code schreiben und verwenden Sie einen Designer, um die Metadaten für die importierte Modelle zu definieren.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)|Zeigt, wie ein neues BDC-Modell zu erstellen.|  
|[Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Zeigt, wie ein vorhandenes Modell in ein SharePoint-Projekt importieren.|  
|[Vorgehensweise: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Beschreibt, wie Zeichenfolgen, die zusammengeführt werden die darin enthaltenen Modellmetadaten bereitzustellen, wenn das Modell von einem Webpart oder einer Webseite genutzt wird.|  
|[Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Zeigt, wie die Funktion eine benutzerdefinierte Assembly einschließt.|  
  
  