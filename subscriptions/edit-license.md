---
title: Bearbeiten von Abonnements im Administratorportal | Microsoft-Dokumentation
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can edit subscription assignments.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 120bf87ddbaf50efa1abe59bac1c2e4616db7737
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="editing-visual-studio-subscription-assignments"></a>Bearbeiten von Visual Studio-Abonnementzuweisungen

## <a name="making-changes-to-subscriber-information"></a>Vornehmen von Änderungen an Abonnenteninformationen
Sie können die Informationen eines Abonnenten bearbeiten, um Fehler zu beheben und Informationen zu aktualisieren. 
**Beachten Sie, dass durch das Bearbeiten der E-Mail-Adresse eines Abonnenten alle vorhandenen Vorteile zurücksetzt werden.**

Klicken Sie für das Bearbeiten eines Abonnenten auf die Auslassungspunkte (...), die neben der E-Mail-Adresse des Abonnenten angezeigt werden, wenn Sie mit der Maus darauf zeigen. Eine Dropdownliste wird angezeigt.  Klicken Sie auf **Bearbeiten**, um die Details des Abonnenten zu ändern. Sie können ebenfalls auf die Zeile des Abonnenten im Raster doppelklicken, um das Bearbeitungsfenster zu öffnen.

   ![Auswählen des zu bearbeitenden Abonnenten](_img\edit-license\select-subscriber.png)

Sie können den Vornamen, den Nachnamen, das Land, die Sprache und die Downloads des Abonnenten aktualisieren. Bearbeiten Sie die Informationen des Abonnenten, und klicken Sie dann auf **Speichern**.

   ![Bearbeiten der Details von Abonnenten](_img\edit-license\edit-subscriber.png)

> [!NOTE]
> Wenn Sie die Abonnementebene für einen Abonnenten ändern müssen, müssen Sie den Benutzer aus dem Portal löschen und erneut hinzufügen. Abonnementebenen können nicht bearbeitet werden.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung

Sie können mehrere Abonnenten gleichzeitig bearbeiten, wenn Sie die Massenbearbeitung verwenden. Diese Funktion wird in erster Linie für Organisationen verwendet, wenn die geschäftlichen E-Mail-Adressen geändert werden, oder wenn eine Organisation sich dafür entschieden hat, den Zugriff auf Downloads zu beschränken. 

> [!IMPORTANT]
> Abonnementebenen (d.h. Enterprise, Professional usw.) und Abonnement-GUIDs können nicht geändert werden.  Wenn Sie etwas hochladen möchten und diese Elemente verändert wurden, schlägt der Upload fehl.  

1.  Navigieren Sie zur Registerkarte „Abonnenten“, um mehrere Abonnenten gleichzeitig zu bearbeiten. Klicken Sie im oberen Bereich des Menübands auf **Massenbearbeitung**. 

    ![Bearbeiten einer Lizenz: Massenbearbeitungen](_img\edit-license\edit-license-bulk-edit.png)

2.  Die Massenbearbeitung verwendet eine Excel-Vorlage, um Änderungen an Abonnenteninformationen vorzunehmen. Klicken Sie im Feld „Massenbearbeitung“ auf **Export this Excel** (Diese Excel-Datei exportieren), um die aktuelle Liste der Abonnenten einschließlich aller Informationen herunterzuladen. 

    ![Bearbeiten einer Lizenz: Exportieren der Massenbearbeitungsliste](_img\edit-license\edit-license-bulk-edit-export.png)

3.  Speichern Sie die Datei lokal, damit Sie diese einfach finden und vor dem Upload erforderliche Änderungen vornehmen können. Für einen erfolgreichen Upload sollten Sie **die Abonnementebene oder Abonnement-GUID nicht bearbeiten**, da dies dazu führt, dass der Upload fehlschlägt. 

4.  Wechseln Sie zum Administratorportal für Visual Studio-Abonnements, und klicken Sie im Dialogfeld „Massenbearbeitung“ auf **Durchsuchen**. Wählen Sie die Excel-Datei aus, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt.

    ![Bearbeiten einer Lizenz: Massenbearbeitungen – Dateiupload](_img\edit-license\edit-license-bulk-file-upload1.png)

5.  Sobald Sie die Datei hochgeladen haben, wird Ihnen eine Benachrichtigung angezeigt, dass der Upload erfolgreich war. 

    ![Bearbeiten einer Lizenz: Massenbearbeitungen – Upload abgeschlossen](_img\edit-license\edit-license-bulk-upload-complete.png)


