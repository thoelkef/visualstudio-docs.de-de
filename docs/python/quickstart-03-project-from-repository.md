---
title: 'Schnellstart: Klonen eines Repositorys in Python-Code in Visual Studio | Microsoft-Dokumentation'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 3ea3afdaa6a7a29bc85c46b6eff0f15c5c91c046
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Schnellstart: Klonen eines Repositorys in Python-Code in Visual Studio

Sobald Sie [die Python-Unterstützung für Visual Studio 2017 installiert haben](installation.md), können Sie ganz leicht ein Repository in Python-Code klonen und daraus ein Projekt erstellen.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Starten Sie Visual Studio.

3. Klicken Sie auf **Ansicht > Team Explorer…**, um das Fenster **Team Explorer** zu öffnen. Von dort können Sie eine Verbindung zu GitHub oder Visual Studio Team Services herstellen oder ein Repository klonen.

    ![Das Team Explorer-Fenster zeigt Visual Studio Team Services, GitHub und das Klonen eines Repositorys.](media/team-explorer.png)

4. Geben Sie im URL-Feld unter **Lokale Git-Repositorys** `https://github.com/gregmalcolm/python_koans` ein, geben Sie einen Ordner für die geklonten Dateien an, und klicken Sie auf **Klonen**.

    > [!Tip]
    > Der Ordner, den Sie in Team Explorer angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in Team Explorer nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

5. Wenn der Klonvorgang abgeschlossen ist, doppelklicken Sie auf den Repositoryordner im unteren Bereich von Team Explorer, um zum Repositorydashboard zu navigieren. Klicken Sie unter **Projektmappen** auf **Neu...**.

    ![Das Fenster „Team Explorer“, in dem ein neues Projekt aus einem Klon erstellt wird](media/team-explorer-new-project.png)

6. Klicken Sie in dem Dialogfeld **Neues Projekt** auf „Aus vorhandenem Python-Code“, geben Sie einen Namen für das Projekt an, legen Sie für **Speicherort** denselben Ordner fest, in dem auch das Repository gespeichert ist, und klicken Sie auf **OK**. Klicken Sie in dem sich öffnenden Assistenten auf **Fertig stellen**.

7. Klicken Sie im Menü auf **Ansicht > Projektmappen-Explorer**.

8. Erweitern Sie im Projektmappen-Explorer den `python3`-Knoten, klicken Sie mit der rechten Maustaste zunächst auf `contemplate_koans.py` und anschließend auf **Als Startprojekt festlegen**. In diesem Schritt meldet Visual Studio, welche Datei beim Ausführen des Projekts verwendet werden soll.

9. Klicken Sie zunächst im Menü auf **Projekt > Eigenschaften** und anschließend auf die Registerkarte **Allgemein**, und legen Sie das **Arbeitsverzeichnis** auf „Python3“ fest. Dieser Schritt ist notwendig, da Visual Studio standardmäßig den Projektstamm als Arbeitsverzeichnis festlegt, anstatt den Speicherort der Startdatei zu verwenden (`python3\contemplate_koans.py` – dies können Sie auch in den Projekteigenschaften sehen). Der Programmcode sucht im Arbeitsverzeichnis nach einer `koans.txt`-Datei. Sie erhalten also einen Fehler, wenn Sie diesen Wert nicht ändern.

    ![Festlegen des Arbeitsverzeichnisses für ein Python-Projekt](media/projects-set-working-directory.png)

10. Drücken Sie STRG+F5, oder klicken Sie auf **Debuggen > Ohne Debuggen starten**, um das Programm auszuführen. Wenn Ihnen `FileNotFoundError` für `koans.txt` angezeigt wird, prüfen Sie die Einstellungen für das Arbeitsverzeichnis im nächsten Schritt erneut.

11. Wenn das Programm erfolgreich ausgeführt wird, zeigt es einen Assertionsfehler in Zeile 17 von `python3/koans/about_asserts.py` an. Dies ist beabsichtigt, da das Programm so entwickelt wurde, dass es Ihnen Python beibringt, indem Sie sämtliche beabsichtigte Fehler beheben müssen. (Weitere Details finden Sie unter [Ruby Koans](http://rubykoans.com/) – der Inspiration für Python Koans.)

    ![Erste Ausgabe des Python Koans-Programms](media/koans-output.png)

12. Öffnen Sie `python3/koans/about_asserts.py`, indem Sie zu der Datei im Projektmappen-Explorer navigieren und darauf doppelklicken. Beachten Sie, dass standardmäßig keine Zeilennummern im Editor erscheinen. Klicken Sie zum Ändern dieser Einstellung auf **Extras > Optionen** und im unteren Bereich des Dialogfelds auf **Alle Einstellungen anzeigen**. Navigieren Sie anschließend zu **Text-Editor > Python > Allgemein**, und klicken Sie auf **Zeilennummern**:

    ![Aktivieren der Zeilennummer für Python-Dateien](media/options-general-line-numbers.png)

13. Korrigieren Sie den Fehler, indem Sie das `False`-Argument in Zeile 17 in `True` ändern. Die Zeile sollte wie folgt lauten:

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Führen Sie das Programm erneut aus, um zu sehen, ob die erste Überprüfung erfolgreich ist, und das Programm wird beim nächsten Koan beendet. Fahren Sie mit dem Korrigieren der Fehler fort, und führen Sie das Programm so oft Sie möchten erneut aus.

> [!Important]
> Mithilfe dieser Schnellstartanleitung haben Sie einen direkten Klon des *python_koans*-Repositorys auf GitHub erstellt. Solche Repositorys werden durch deren Autoren vor direkten Änderungen geschützt, sodass ein möglicher Änderungsversuch fehlschlägt. Tatsächlich forken Entwickler solche Repositorys in ihre GitHub-Kontos. Nehmen Sie die Änderungen in diesem Konto vor, und erstellen Sie anschließend Pull Requests, um sie an das ursprüngliche Repository zu übermitteln. Diese Schritte werden in [Tutorial Step 6 – Working with Git (Tutorial, Schritt 6: Arbeiten mit Git)](vs-tutorial-01-06.md) beschrieben.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Working with Python in Visual Studio (Tutorial: Arbeiten mit Python in Visual Studio)](vs-tutorial-01-01.md)

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Umgebung für einen vorhandenen Python-Interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installation.md)
- [Installationsspeicherorte](installation.md#install-locations)
