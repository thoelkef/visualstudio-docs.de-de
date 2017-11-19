---
title: "Seite \"Veröffentlichen\", Projekt-Designer (Office-Entwicklung in Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
ms.assetid: 94d9bdf1-84fa-4e26-8ece-a1a0dabda5ea
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ce726d9d86bd57e5cf245010212545f0055c8ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Veröffentlichungsseite, Projekt-Designer (Office-Entwicklung in Visual Studio)
  Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die Bereitstellung verwendet.  
  
 Wählen Sie zum Aufrufen der Seite das Projekt im **Projektmappen-Explorer**aus, und klicken Sie anschließend im Menü **Projekt** auf *Projektname* **Eigenschaften**. Wenn die Seite **Veröffentlichen** nicht angezeigt wird, wählen Sie die Registerkarte **Veröffentlichen** aus.  
  
> [!NOTE]  
>  Sie können auch den Veröffentlichungsort im **Veröffentlichungs-Assistenten**festlegen. Weitere Informationen finden Sie unter [Gewusst wie: Veröffentlichen einer Office-Projektmappe mithilfe von ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Speicherort des Veröffentlichungsordners (Website, FTP-Server oder Dateipfad)**  
 Erforderlich.  
  
 Der Speicherort des Veröffentlichungsordners ist das Verzeichnis, in das Visual Studio die Projektmappendateien kopiert, z. B. Manifeste, Assemblys und andere Dateien aus dem Build. Sie benötigen Schreibzugriff auf dieses Verzeichnis.  
  
 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokalen sein (*c:\foldername\publishfolder*), einen relativen (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\servername\foldername* oder http://*Servername/Ordnername*).  
  
 Standardmäßig wird *http://localhost/Projektname/* als Speicherort für die Veröffentlichung verwendet, wenn IIS installiert ist. Wenn IIS nicht installiert ist, wird das Verzeichnis „publish\“ verwendet.  
  
 **URL des Installationsordners**  
 Optional.  
  
 Die URL des Installationsordners ist das Verzeichnis, über das der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Als Pfad kann derselbe Pfad wie für den Speicherort des Veröffentlichungsordners verwendet werden, aber dies ist nicht unbedingt erforderlich.  
  
 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokalen sein (*c:\foldername\publishfolder*), einen relativen (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\servername\foldername* oder http://*Servername/Ordnername*). Alle HTTP/HTTPS-Speicherorte müssen mit US-ASCII-Zeichen erstellt werden. Unicode-Zeichen werden nicht unterstützt.  
  
 Wenn der Installationspfad festgelegt ist, müssen sich die Anpassungsdateien an diesem Speicherort befinden, damit Benutzer die Anpassung installieren können. Der Speicherort sollte nur festgelegt werden, wenn Sie den endgültigen Speicherort für die Bereitstellung kennen.  
  
 Lassen Sie dieses Feld leer, wenn sich die Installationsdateien an einem Speicherort befinden, der relativ zum Dokument oder Setupprogramm angegeben ist, z. B. bei der Option „CD“.  
  
 Dieser Wert kann später von einem Administrator zugewiesen werden. Weitere Informationen finden Sie unter [Gewusst wie: Ändern des Installationspfads einer Office-Projektmappe](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Erforderliche Komponenten**  
 Die erforderlichen Komponenten können in das Setupprogramm einbezogen oder bei Bedarf während der Installation heruntergeladen werden.  
  
-   **Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten bei Microsoft herunterladen.  
  
-   **Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten im Installationsprogramm verpacken. Das Einbeziehen der Dateien für die erforderlichen Komponenten in das Setupprogramm erhöht die Größe der Projektmappe.  
  
-   **Erforderliche Komponenten von folgendem Speicherort herunterladen**: Mithilfe dieser Option können Sie die erforderlichen Komponenten für Endbenutzer gesondert als weiteres Setupprogramm auf einer Webseite oder Netzwerkfreigabe zur Verfügung stellen.  
  
 **Updates**  
 Das Aktualisierungsintervall bestimmt, wie oft die Projektmappe nach Updates sucht. Standardmäßig wird die Prüfung alle sieben Tage ausgeführt.  
  
 Wenn bei jeder Anpassung auf Dokumentebene oder beim Laden eines VSTO-Add-Ins auf Updates geprüft wird, würde das System auf dem neuesten Stand bleiben, aber es würde ebenfalls die Leistung beim Start beeinträchtigen.  
  
 Wenn Sie die Bereitstellung mithilfe einer CD oder eines Wechsellaufwerks vornehmen, legen Sie die Option **Nie nach Updates suchen**fest.  
  
 **Optionen (Beschreibung)**  
 Die Veröffentlichungsoptionen für die folgenden Eigenschaften können festgelegt werden:  
  
-   Sprache für Veröffentlichung: Das Gebietsschema der Office-Projektmappe.  
  
-   Herausgebername: Der Firmen- oder Entwicklername, wie er unter **Software** oder **Programme und Funktionen**angezeigt wird.  
  
-   Produktname: Der Name der Office-Projektmappe, wie er unter **Software** oder **Programme und Funktionen**angezeigt wird.  
  
-   Support-URL: Der Pfad für Endbenutzer, um sich an den technischen Support für die Office-Projektmappe zu wenden.  
  
 **Optionen (Office-Einstellungen)**  
 Die Veröffentlichungsoptionen für die folgenden Eigenschaften können festgelegt werden:  
  
-   Projektmappenname: Der Name der Office-Projektmappe, wie er in der Office-Anwendung angezeigt wird.  
  
-   Beschreibung: Die Beschreibung der Office-Projektmappe, wie sie in der Office-Anwendung angezeigt wird.  
  
-   VSTO-Add-In-Ladeverhalten.  
  
    -   Beim Start laden: Gibt an, dass das VSTO-Add-In beim Starten der Office-Anwendung geladen wird.  
  
    -   Bedarfsgesteuert laden: Gibt an, dass das VSTO-Add-In nur geladen wird, wenn es für die Anwendung erforderlich ist, wenn z. B. ein Benutzer auf ein Benutzeroberflächenelement klickt, das auf Funktionen im VSTO-Add-In zurückgreift.  
  
 **Sprache für Veröffentlichung**  
 Diese Option legt die Sprache für die Microsoft-Softwarelizenzbedingungen fest und bezieht die Language Packs in die Liste der erforderlichen Komponenten ein. Sie wirkt sich nicht auf die Sprache der Anpassung aus. Die Sprache im Setupprogramm wird durch die installierten Sprachen von Visual Studio bestimmt.  
  
 Weitere Informationen zum Ändern der **Sprache für Veröffentlichung**finden Sie unter [How to: Change the Publish Language for a ClickOnce Application](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
 **Veröffentlichungsversion**  
 Legt die Versionsnummer für die Anpassung fest. Wenn die Versionsnummer geändert wird, erfolgt die Veröffentlichung der Anwendung als Update. Für jede Version wird während des Buildprozesses ein neuer Ordner erstellt, um das Überschreiben der zuvor veröffentlichten Version zu verhindern. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann bis zu fünf Ziffern umfassen.  
  
 **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen**  
 Optional. Wenn aktiviert (Standardeinstellung), wird der Teil **Revision** der Versionsnummer bei jeder Veröffentlichung der Anpassung um eins erhöht. Dies bewirkt, dass die Anpassung als Update veröffentlicht wird.  
  
 **Jetzt veröffentlichen**  
 Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertig stellen** im **Veröffentlichungs-Assistent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Erforderliche Komponenten für Office-Projektmappen für die Bereitstellung](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  