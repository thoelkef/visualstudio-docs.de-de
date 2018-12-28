---
title: Veröffentlichungsseite, Projekt-Designer (Office-Entwicklung in Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66cb2c4cb15dfad2fa9d3a0508bd2d023360ee90
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803713"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Veröffentlichungsseite, Projekt-Designer (Office-Entwicklung in Visual Studio)
  Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die Bereitstellung verwendet.

 Wählen Sie zum Aufrufen der Seite das Projekt im **Projektmappen-Explorer**aus, und klicken Sie anschließend im Menü **Projekt** auf *Projektname* **Eigenschaften**. Wenn die Seite **Veröffentlichen** nicht angezeigt wird, wählen Sie die Registerkarte **Veröffentlichen** aus.

> [!NOTE]
>  Sie können auch den Veröffentlichungsort im **Veröffentlichungs-Assistenten**festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer Office-Projektmappe mit ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>UIElement-Liste
 **Speicherort des Veröffentlichungsordners (Website, ftp-Server oder Dateipfad)** erforderlich sind.

 Der Speicherort des Veröffentlichungsordners ist das Verzeichnis, in das Visual Studio die Projektmappendateien kopiert, z. B. Manifeste, Assemblys und andere Dateien aus dem Build. Sie benötigen Schreibzugriff auf dieses Verzeichnis.

 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokale sein (*c:\foldername\publishfolder*), relativer (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\servername\foldername* oder http://<em>Servername/Ordnername</em>).

 Standardmäßig ist der Ort der Veröffentlichung *http://localhost/projectname/* Wenn IIS installiert ist, oder die *veröffentlichen\\*  Verzeichnis, wenn Sie nicht IIS installiert haben.

 **URL des Installationsordners** Optional.

 Die URL des Installationsordners ist das Verzeichnis, über das der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Als Pfad kann derselbe Pfad wie für den Speicherort des Veröffentlichungsordners verwendet werden, aber dies ist nicht unbedingt erforderlich.

 Optionen umfassen den lokalen Computer, eine UNC-Dateifreigabe oder eine HTTP/HTTPS-Website. Der Pfad kann lokale sein (*c:\foldername\publishfolder*), relativer (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\servername\foldername* oder http://<em>Servername/Ordnername</em>). Alle HTTP/HTTPS-Speicherorte müssen mit US-ASCII-Zeichen erstellt werden. Unicode-Zeichen werden nicht unterstützt.

 Wenn der Installationspfad festgelegt ist, müssen sich die Anpassungsdateien an diesem Speicherort befinden, damit Benutzer die Anpassung installieren können. Der Speicherort sollte nur festgelegt werden, wenn Sie den endgültigen Speicherort für die Bereitstellung kennen.

 Lassen Sie dieses Feld leer, wenn sich die Installationsdateien an einem Speicherort befinden, der relativ zum Dokument oder Setupprogramm angegeben ist, z. B. bei der Option „CD“.

 Dieser Wert kann später von einem Administrator zugewiesen werden. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Installationspfads einer Office-Projektmappe](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Erforderliche Komponenten** die erforderlichen Komponenten im Setup-Programm enthalten oder bei Bedarf während der Installation heruntergeladen werden können.

- **Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**: Verwenden Sie diese Option, um die erforderlichen Komponenten von Microsoft herunterladen.

- **Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**: Verwenden Sie diese Option, um die erforderlichen Komponenten im Installationsprogramm verpacken. Das Einbeziehen der Dateien für die erforderlichen Komponenten in das Setupprogramm erhöht die Größe der Projektmappe.

- **Erforderliche Komponenten von folgendem Speicherort herunterladen**: Verwenden Sie diese Option, um die erforderlichen Komponenten verfügbar für Endbenutzer gesondert als weiteres Setupprogramm auf einer Webseite oder Netzwerkfreigabe stellen.

  **Updates** das Aktualisierungsintervall bestimmt, wie oft die Projektmappe nach Updates sucht. Standardmäßig wird die Prüfung alle sieben Tage ausgeführt.

  Wenn bei jeder Anpassung auf Dokumentebene oder beim Laden eines VSTO-Add-Ins auf Updates geprüft wird, würde das System auf dem neuesten Stand bleiben, aber es würde ebenfalls die Leistung beim Start beeinträchtigen.

  Wenn Sie die Bereitstellung mithilfe einer CD oder eines Wechsellaufwerks vornehmen, legen Sie die Option **Nie nach Updates suchen**fest.

  **Optionen (Beschreibung)** die Veröffentlichungsoptionen für die folgenden Eigenschaften können festgelegt werden:

- Sprache für Veröffentlichung: Das Gebietsschema der Office-Projektmappe.

- Herausgebername: Der Firmen- oder Entwicklername, wie er unter **Software** oder **Programme und Funktionen**angezeigt wird.

- Produktname: Der Name der Office-Projektmappe, wie er unter **Software** oder **Programme und Funktionen**angezeigt wird.

- Support-URL: Der Pfad für Endbenutzer, um sich an den technischen Support für die Office-Projektmappe zu wenden.

  **Optionen (Office-Einstellungen)** die Veröffentlichungsoptionen für die folgenden Eigenschaften können festgelegt werden:

- Projektmappenname: Der Name der Office-Projektmappe, wie er in der Office-Anwendung angezeigt wird.

- Beschreibung: Die Beschreibung der Office-Projektmappe, wie sie in der Office-Anwendung angezeigt wird.

- VSTO-Add-In-Ladeverhalten.

  -   Beim Start laden: Gibt an, dass das VSTO-Add-In beim Starten der Office-Anwendung geladen wird.

  -   Bedarfsgesteuert laden: Gibt an, dass das VSTO-Add-In nur geladen wird, wenn es für die Anwendung erforderlich ist, wenn z. B. ein Benutzer auf ein Benutzeroberflächenelement klickt, das auf Funktionen im VSTO-Add-In zurückgreift.

  **Sprache für Veröffentlichung** diese Option wird die Sprache der Microsoft Software-Lizenzbedingungen, und bezieht die Language Packs in der Liste der Voraussetzungen. Sie wirkt sich nicht auf die Sprache der Anpassung aus. Die Sprache im Setupprogramm wird durch die installierten Sprachen von Visual Studio bestimmt.

  Weitere Informationen zur Vorgehensweise beim Ändern der **Sprache für Veröffentlichung**, finden Sie unter [Vorgehensweise: Ändern Sie die Veröffentlichungssprache einer ClickOnce-Anwendung](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Veröffentlichungsversion** legt die Versionsnummer für die Anpassung fest. Wenn die Versionsnummer geändert wird, erfolgt die Veröffentlichung der Anwendung als Update. Für jede Version wird während des Buildprozesses ein neuer Ordner erstellt, um das Überschreiben der zuvor veröffentlichten Version zu verhindern. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann bis zu fünf Ziffern umfassen.

  **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen** Optional. Wenn aktiviert (Standardeinstellung), wird der Teil **Revision** der Versionsnummer bei jeder Veröffentlichung der Anpassung um eins erhöht. Dies bewirkt, dass die Anpassung als Update veröffentlicht wird.

  **Jetzt veröffentlichen** veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertig stellen** im **Veröffentlichungs-Assistent**.

## <a name="see-also"></a>Siehe auch

- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
- [Bereitstellen einer Office-Projektmappe mit ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Erforderliche Komponenten für Office-Projektmappen für die Bereitstellung](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
