---
title: Bearbeiten von Abonnements im Verwaltungsportal | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Abonnementzuweisungen bearbeiten können.
ms.openlocfilehash: cd4bb40599ff242e20ba0e38fb561bde7d3f1823
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263275"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Bearbeiten von Visual Studio-Abonnementzuweisungen
Als Abonnementadministrator können Sie Änderungen an den Abonnements vornehmen, die Personen innerhalb Ihrer Organisation zugewiesen sind.  Dieser Artikel beschreibt die Arten von Änderungen, die Sie vornehmen können, und enthält die notwendigen Schritte.

   > [!NOTE]
   > Wenn Sie Abonnementdetails für Abonnenten ändern müssen, der über eine Azure Active Directory-Gruppe zugewiesen wurde, müssen Sie diese aus der Gruppe entfernen und im Verwaltungsportal einzeln hinzufügen.  

## <a name="change-subscriber-information"></a>Eingeben der Abonnenteninformationen
Sie können die Informationen eines Abonnenten bearbeiten, um Fehler zu beheben und Informationen zu aktualisieren.

Klicken Sie für das Bearbeiten eines Abonnenten auf die Auslassungspunkte (...), die neben der E-Mail-Adresse des Abonnenten angezeigt werden, wenn Sie mit der Maus darauf zeigen. Eine Dropdownliste wird angezeigt.  Klicken Sie auf **Bearbeiten**, um die Details des Abonnenten zu ändern. 
> [!div class="mx-imgBorder"]
> ![Auswählen des zu bearbeitenden Abonnenten](_img/edit-license/select-subscriber.png)

Sie können Vornamen, Nachnamen, Abonnementebene, E-Mail-Adresse, Land/Region, Sprache, Downloads und Referenz für den Abonnenten aktualisieren. Bearbeiten Sie die Informationen zum Abonnenten, und klicken Sie dann auf **Speichern**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung
Sie können mehrere Abonnenten gleichzeitig bearbeiten, wenn Sie die Massenbearbeitung verwenden. Diese Funktion wird in erster Linie für Organisationen verwendet, wenn die geschäftlichen E-Mail-Adressen geändert werden, oder wenn eine Organisation sich dafür entschieden hat, den Zugriff auf Downloads zu beschränken.

   > [!IMPORTANT]
   > Abonnementebenen (d. h. Enterprise, Professional usw.) und Abonnement-GUIDs können nicht über eine Massenbearbeitung geändert werden.  Wenn Sie Ihren Benutzern bestimmte Abonnement-GUIDs zuweisen müssen, verwenden Sie den Prozess zum Hinzufügen von Benutzern, indem Sie die Abonnement-ID auswählen. Wenn Sie versuchen, einen Upload auszuführen, bei dem diese Elemente in der Massenbearbeitungsvorlage geändert wurden, kommt es beim Upload zu einem Fehler.

1. Navigieren Sie zur Registerkarte „Abonnenten“, um mehrere Abonnenten gleichzeitig zu bearbeiten. Klicken Sie im oberen Bereich des Menübands auf **Massenbearbeitung**.

2. Die Massenbearbeitung verwendet eine Excel-Vorlage, um Änderungen an Abonnenteninformationen vorzunehmen. Klicken Sie im Feld „Massenbearbeitung“ auf **Export this Excel** (Diese Excel-Datei exportieren), um die aktuelle Liste der Abonnenten einschließlich aller Informationen herunterzuladen.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Exportieren der Massenbearbeitungsliste](_img/edit-license/edit-license-bulk-edit-export.png)

3. Speichern Sie die Datei lokal, damit Sie diese einfach finden und vor dem Upload erforderliche Änderungen vornehmen können. Für einen erfolgreichen Upload darf die **Abonnementebene oder Abonnement-GUID nicht in der Massenbearbeitungsdatei bearbeitet werden**, da dies zu einem Fehler beim Upload führt.

4. Wechseln Sie zum Administratorportal für Visual Studio-Abonnements, und klicken Sie im Dialogfeld „Massenbearbeitung“ auf **Durchsuchen**. Wählen Sie die Excel-Datei aus, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Massenbearbeitungen – Dateiupload](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Sobald Sie die Datei hochgeladen haben, wird Ihnen eine Benachrichtigung angezeigt, dass der Upload erfolgreich war. Jetzt sind Ihre Änderungen in den Abonnenteninformationen zu enthalten.

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Sie müssen eine bestimmte Abonnement-ID zuweisen? Lesen Sie „Zuweisen einer Abonnement-ID“. 
- Um ein bestimmtes Abonnement zu finden, informieren Sie sich unter [Suchen nach einem Abonnement](search-license.md).
- Müssen Sie eine Liste all Ihrer Abonnements erstellen?  Informieren Sie sich unter [Exportieren von Abonnements](exporting-subscriptions.md).


