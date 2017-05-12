---
title: "Erstellen eines Business Data Connectivity-Modells"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Modell"
  - "SharePoint-Entwicklung in Visual Studio, Business Data Connectivity-Dienst"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Erstellen eines Business Data Connectivity-Modells
  Sie können ein Business Data Connectivity \(BDC\)\-Modell erstellen oder mit Visual Studio ein vorhandenes BDC\-Modell anpassen.  Jedes SharePoint\-Projekt kann jeweils nur ein Modell enthalten.  Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Erstellen eines neuen Modells  
 Wenn Sie ein neues Modell erstellen möchten, erstellen Sie ein Projekt vom Typ **Business Data Connectivity\-Modell**, oder fügen Sie einem **leeren SharePoint\-Projekt** ein Element **Business Data Connectivity\-Modell** hinzu.  
  
> [!NOTE]  
>  Auf Ihrem Computer muss [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installiert sein.  
  
 Visual Studio fügt dem Projekt einen Ordner hinzu.  Dieser Ordner weist den Namen auf, den Sie im Dialogfeld **Neues Element hinzufügen** für das Element **Business Data Connectivity\-Modell** angeben.  Wenn Sie ein neues Projekt vom Typ **Business Data Connectivity\-Modell** erstellen, weist Visual Studio dem Ordner den Namen **BdcModel1** zu.  
  
 Visual Studio fügt dem neuen Ordner die folgenden Dateien hinzu:  
  
|Datei|**Beschreibung**|  
|-----------|----------------------|  
|Modelldefinitionsdatei|Enthält XML, das die Entitäten, Methoden, LOB\-Systemobjekte \(Line\-of\-Business\) und andere Metadaten definiert, die das Modell beschreiben.<br /><br /> Ändern Sie die Metadaten in dieser Datei mit dem BDC\-Designer, dem **BDC\-Explorer**, dem Fenster **BDC\-Methodendetails** und dem Fenster **Eigenschaften**.|  
|Codedatei für den Entitätsdienst|Enthält Methoden, die Instanzen der Standardentität abrufen, aktualisieren und löschen.|  
  
 Um die Eigenschaften einer Entität zu definieren, bearbeiten Sie die Entitätscodedatei.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Um Instanzen einer Entität abzurufen, zu aktualisieren und zu löschen, fügen Sie der Codedatei des Entitätsdiensts Code hinzu.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Wenn Sie das Projekt kompilieren, erstellt Visual Studio eine Assembly.  Stellen Sie sicher, dass Sie dem Projekt keine weiteren Elemente hinzufügen, die der Projektassembly Code hinzufügen \(Beispiel: ein Element **Sequenzieller Workflow** oder ein Element **Webpart**\).  Der Code für das betreffende Element wird nicht ausgeführt, wenn Sie die Lösung bereitstellen, da das Lösungspaket die Assembly nicht in den globalen Assemblycache kopiert.  Das Lösungspaket stellt die Assembly nur in der BDC\-Datenbank in SharePoint bereit.  
  
> [!NOTE]  
>  Wenn Sie das Projekt debuggen, kopiert Visual Studio die Assembly an beide Positionen auf dem lokalen Computer.  
  
## Hinzufügen eines vorhandenen Modells  
 Sie können ein Modell importieren, das mit anderen Tools wie dem SharePoint\-Designer erstellt wurde.  In den folgenden Situationen können Sie beispielsweise ein vorhandenes Modell in das Projekt importieren:  
  
-   Zum Anpassen eines Modells, das bereits in einer SharePoint\-Serverfarm bereitgestellt wurde.  
  
-   Zum Verpacken und Bereitstellen eines vorhandenen Modells für mehrere SharePoint\-Serverfarmen.  
  
 In beiden Fällen sind die LOB\-Systeme, die im importierten Modell definiert wurden, nicht betroffen und funktionieren weiterhin wie erwartet.  Um einem SharePoint\-Projekt ein vorhandenes Modell hinzuzufügen, verwenden Sie das Visual Studio\-Dialogfeld **Vorhandenes Element hinzufügen**.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Sie können dem importierten Modell ein LOB\-System vom Typ .NET Framework\-Assembly hinzufügen, indem Sie in **.NET\-Assembly\-LobSystem hinzufügen** eine Option auswählen.  Dies ermöglicht es Ihnen, benutzerdefinierten Code zu schreiben und einen Designer zu verwenden, um die Metadaten für das importierte Modell zu definieren.  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)|Zeigt, wie ein neues BDC\-Modell erstellt wird.|  
|[Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Zeigt, wie ein vorhandenes Modell in ein SharePoint\-Projekt importiert wird.|  
|[Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Beschreibt, wie Zeichenfolgen bereitgestellt werden, die mit Modellmetadaten zusammengeführt werden, wenn das Modell von einem Webpart oder einer Webseite verwendet wird.|  
|[Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Zeigt, wie eine benutzerdefinierte Assembly in die Funktion eingeschlossen wird.|  
  
  