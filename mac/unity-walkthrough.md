---
title: Erste Schritte beim Erstellen von Spielen mit Unity in Visual Studio für Mac
description: Erste Schritte mit Unity und Visual Studio für Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: 8f14d21468336dba220a76ad8978f136d50f96f1
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836159"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Erste Schritte beim Erstellen von Spielen mit Unity in Visual Studio für Mac 

Unity ist eine Spiele-Engine, die Ihnen ermöglicht, Entwickeln von Spielen in C#. In dieser exemplarischen Vorgehensweise wird gezeigt, wie für den Einstieg in die Entwicklung und debugging Unity-Spielen mit Visual Studio für Mac und Visual Studio für Mac-Tools für Unity-Erweiterung, zusammen mit der Unity-Umgebung.

Visual Studio für Mac-Tools für Unity ist eine kostenlose Erweiterung, die mit Visual Studio für Mac installiert Sie können die Unity-Entwickler die Produktivitätsfeatures von Visual Studio für Mac, einschließlich hervorragende Unterstützung für IntelliSense, Debuggen und weitere Funktionen nutzen.

## <a name="objectives"></a>Ziele

> [!div class="checklist"]
> * Erfahren Sie mehr über die Unity-Entwicklung mit Visual Studio für Mac

## <a name="prerequisites"></a>Erforderliche Komponenten

- Visual Studio für Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition oder höher ([https://store.unity.com](https://store.unity.com/), auszuführende unity.com-Konto erforderlich)

## <a name="intended-audience"></a>Zielgruppe

Diese Übungseinheit richtet sich an Entwickler, die mit vertraut sind C#, obwohl tagtäglich nicht erforderlich ist.

## <a name="task-1-creating-a-basic-unity-project"></a>Aufgabe 1: Erstellen ein einfaches Unity-Projekt

1. Starten Sie **Unity**. Melden Sie sich, wenn angefordert.

2. Klicken Sie auf **neue**.

    ![Schaltfläche "Neu" in unity](media/unity-image1.png)

3. Legen Sie die **Projektname** zu **"UnityLab"** , und wählen Sie **3D**. Klicken Sie auf **projekterstellung**.

    ![Bildschirm "Neues Projekt" erstellen](media/unity-image2.png)

4. Entdecken Sie jetzt auf das standardmäßige Unity-Oberfläche. Sie hat die szenenhierarchie mit Spielobjekte, auf der linken Seite eine 3D-Ansicht der leere Szene in der Mitte, ein Projektfensterbereich zur Dateien auf den nach unten, und der Inspektor und Dienste auf der rechten Seite angezeigt. Natürlich ist es, als noch viel mehr, aber dies sind einige der wichtigeren Komponenten.

    ![leere Unity-Oberfläche](media/unity-image3.png)

5. Für Entwickler, die noch nicht mit Unity, alle Elemente, die in Ihrer app ausgeführt wird. befindet sich innerhalb des Kontexts einer **Szene**. Eine Szenendatei ist eine einzelne Datei, die alle Sorten der Metadaten zu den Ressourcen, die im Projekt verwendet wird, für die aktuelle Szene und deren Eigenschaften enthält. Wenn Sie Ihre app für eine Plattform packen, endet die resultierende app wird eine Auflistung von einer oder mehrerer Szenen sowie plattformabhängigen Code, die, den Sie hinzufügen. Sie können beliebig viele Szenen wie gewünscht in einem Projekt verwenden.

6. Die neue Szene enthält lediglich eine Kamera und eine gerichtetes Licht. Erfordert eine Szene ein **Kamera** für alle Elemente angezeigt werden und ein **Audio Listener** für alle Elemente akustische sein. Diese Komponenten werden angefügt, um eine **"gameobject"** .

7. Wählen Sie die **Main Camera** -Objekt aus der **Hierarchie** Bereich.

    ![in den Hierarchiebereich hervorgehoben Hauptkamera-Objekt](media/unity-image4.png)

8. Wählen Sie die **Inspektor** Bereich von der rechten Seite des Fensters, um die Eigenschaften zu überprüfen. Kameraeigenschaften zählen Transformationsinformationen, Hintergrund, Projektionstyp, Sichtfeld und So weiter. Eine Audio Listener-Komponente wurde ebenfalls standardmäßig hinzugefügt, die Szene Audio von einem virtuellen Mikrofon angefügt werden, bis zur Kamera im Wesentlichen rendert.

    ![Bereich der Eigenschaftenanalyse](media/unity-image5.png)

9. Wählen Sie die **gerichtetes Licht** Objekt. Dies bietet Licht, um der Szene, sodass Komponenten wie der Shader weiß, wie Objekte rendern.

    ![Richtung ein Lichtobjekt hervorgehoben](media/unity-image6.png)

10. Verwenden der **Inspektor** zu erkennen, dass es sich um allgemeine Beleuchtungseigenschaften, einschließlich Typ, Farbe, Intensität, Schattentyp usw. enthält.

    ![Eigenschaften im Bereich der Eigenschaftenanalyse ansehen](media/unity-image7.png)

11. Es ist wichtig, darauf hinweisen, dass Projekte in Unity etwas anders aus ihrer Visual Studio für Mac-Entsprechungen sind. In der **Projekt** Registerkarte unten auf der rechten Maustaste auf die **Assets** Ordner, und wählen **im Finder zeigen**.

    ![im Finder kontextaktion anzeigen](media/unity-image8.png)

12. Projekte enthalten **Assets**, **Bibliothek**, **ProjectSettings**, und **Temp** Ordnern, wie Sie sehen. Ist Sie jedoch die einzige, der in der Benutzeroberfläche angezeigt wird, wird die **Assets** Ordner. Die **Bibliothek** Ordner ist der lokale Zwischenspeicher für importierte Assets, er enthält alle Metadaten für Objekte. Die **ProjectSettings** Ordner speichert die Einstellungen, die Sie konfigurieren können. Die **Temp** Ordner für temporäre Dateien aus Mono und Unity während des Buildprozesses verwendet wird. Es gibt auch eine Projektmappendatei, die Sie in Visual Studio für Mac öffnen können (**UnityLab.sln** hier).

    ![Objekte im Finder zeigen](media/unity-image9.png)

13. Schließen der **Finder** Fenster, und wechseln Sie zurück zur **Unity**.

14. Die **Assets** Ordner enthält alle Ihre Assets-Grafiken, Code, Audio usw. Es ist jetzt leer, aber jede einzelne Datei, die Sie in Ihrem Projekt zu importieren, hier einfügen. Dies ist immer der Ordner der obersten Ebene in der **Unity-Editor**. Aber immer hinzufügen und entfernen Sie Dateien über die Unity-Oberfläche (oder Visual Studio für Mac) und nie über das Dateisystem direkt.

    ![Ordner "Assets" in unity](media/unity-image10.png)

15. Die **"gameobject"** ist ein wesentlicher Bestandteil-Entwicklung in Unity wie fast alles, was von diesem Typ, einschließlich der Modelle, Beleuchtung, Partikelsysteme und So weiter abgeleitet wird. Fügen Sie einen neuen **Cube** Objekt in die Szene über die **"gameobject" > 3D-Objekt > Cube** Menü.

    ![Cube-Objekt in der Szene](media/unity-image11.png)

16. Nehmen Sie einen kurzen Blick auf die Eigenschaften der neuen **"gameobject"** und sehen Sie, dass sie einen Namen, Tag, Ebene und Transformation verfügt. Diese Eigenschaften gelten für alle **"gameobjects"** . Darüber hinaus wurden verschiedene Komponenten angefügt, um die **Cube** zu mesh Funktionen erforderlich sind, Filter-, Box-Collider und Renderer.

    ![Spiele-Objekt – Eigenschaften](media/unity-image12.png)

17. Benennen Sie die **Cube** -Objekt, das mit dem Namen **"Cube"** standardmäßig auf **"Enemy"** . Achten Sie darauf, drücken die **EINGABETASTE** um die Änderung zu speichern. Dies ist der gegnerischen Cube in unser einfaches Spiel wird.

    ![Cube-Objekteigenschaft umbenennen](media/unity-image13.png)

18. Fügen Sie ein weiteres **Cube** -Objekt in der Szene mithilfe des gleichen Prozesses wie oben beschrieben, und nennen Sie diese **"Player"** .

    ![Benennen Sie die zweite Cubeobjekt](media/unity-image14.png)

19. Markieren Sie das Player-Objekt **"Player"** auch (finden Sie unter **Tag** Dropdown-Steuerelement direkt unter dem Feld "Name"). Wir verwenden dies im gegnerischen Skript, damit das Player-spielobjekt zu suchen.

    ![Markieren das Player-Objekt](media/unity-image15.png)

20. In der **Szene** anzeigen, die das Player-Objekt, von der gegnerischen Objekt entlang der Z-Achse, die mit der Maus verschieben. Sie können auf der Z-Achse verschieben, wählen und ziehen den Cube durch seine **roten** panel in Richtung der **blaue** Zeile. Da der Cube befindet sich im 3D-Raum, aber nur kann in 2D jedes Mal gezogen werden, ist die Achse, die auf der Sie ziehen, besonders wichtig.

    ![Szene Ansicht mit cube](media/unity-image16.png)

21. Verschieben Sie den Cube an, nach unten und rechts auf der Achse. Aktualisiert die **"Transform.Position"** -Eigenschaft in der **Inspektor**. Achten Sie darauf, ziehen an einem Speicherort auf ähnliche Weise, was hier gezeigt hat, um spätere Schritte in der testumgebung zu erleichtern.

    ![Verschieben Sie einen Cube auf der Achse](media/unity-image17.png)

22. Jetzt können Sie Code, um die gegnerischen Logik zu unterstützen, so, dass es sich um den Spieler ausübt hinzufügen. Mit der rechten Maustaste die **Assets** Ordner in der **Projekt** aufzufüllen, und wählen Sie **erstellen > C# Skript**.

    ![C#Kontext-Skriptaktion](media/unity-image18.png)

23. Benennen Sie den neuen C# Skript **""enemyai ""** .

    ![C#-Skript](media/unity-image19.png)

24. Anzufügende Skripts Spielobjekte ziehen Sie das neu erstellte Skript auf die **Feind** -Objekt in der **Hierarchie** Bereich. Dieses Objekt wird jetzt Verhaltensweisen dieses Skript verwenden.

    ![Hinzufügen von Skripts spielobjekt mit Hervorhebung](media/unity-image20.png)

25. Wählen Sie **Datei > Speichern Szenen** um die aktuelle Szene zu speichern. Nennen Sie sie **"MyScene"** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Aufgabe 2: Arbeiten mit Visual Studio für Mac-Tools für Unity

1. Die beste Methode zum Bearbeiten C# Code ist die Verwendung von Visual Studio für Mac. Sie können Unity Verwendung von Visual Studio für Mac als der Standardhandler konfigurieren. Wählen Sie **Unity > Voreinstellungen**.

2. Wählen Sie die **externe Tools** Registerkarte. Von der **External Script Editor** Dropdownliste wählen **Durchsuchen** , und wählen Sie **Anwendungen/Visual Studio.app**. Auch wenn es bereits eine **Visual Studio** aus, wählen Sie einfach, die.

    ![Registerkarte "externe Tools" in den Voreinstellungen](media/unity-image21.png)

3. Unity ist die Verwendung konfiguriert **Visual Studio für Mac** zur skriptbearbeitung. Schließen der **Unity Preferences** Dialogfeld.

    ![Visual Studio, die in den Voreinstellungen ausgewählt](media/unity-image22.png)

4. Doppelklicken Sie auf **EnemyAI.cs** , öffnen Sie ihn in **Visual Studio für Mac**.

    ![Gegnerischen Asset in Unity ausgewählt](media/unity-image23.png)

5. Visual Studio-Projektmappe ist einfach. Er enthält eine **Assets** Ordner (die gleiche aus **Finder**) und die **EnemyAI.cs** Skripts, die zuvor erstellt haben. In Projekten auf komplexere sieht Hierarchie wahrscheinlich unterscheiden, was Sie in Unity finden Sie unter.

    ![Projektmappenpad in Visual Studio für Mac](media/unity-image24.png)

6. **EnemyAI.cs** im Editor geöffnet ist. Das erste Skript enthält nur die Stubs für die **starten** und **Update** Methoden.

7. Ersetzen Sie den anfänglichen gegnerischen Code durch den folgenden Code ein.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;
        
        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Nehmen Sie hier einen kurzen Blick auf das einfache gegnerischen Verhalten, das definiert wird. In der **starten** -Methode rufen wir einen Verweis auf das Player-Objekt (durch seine-Tag), als auch die **transformieren**. In der **Update** -Methode, die für jedes Bild aufgerufen wird, wechselt der Feind in Richtung das Player-Objekt. Verwenden die Schlüsselwörter und Namen farbcodierung, um die Codebasis in Visual Studio für Mac zu vereinfachen

9. Speichern Sie die Änderungen zum gegnerischen-Skript im **Visual Studio für Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Aufgabe 3: Debuggen des Unity-Projekts

1. Legen Sie einen Haltepunkt in der ersten Zeile des Codes in der **starten** Methode. Sie können entweder auf die am Rand des Editors an der Ziel Zeile oder direkt die Cursorposition auf die Zeile, und drücken Sie **F9**.

    ![Festlegen des Haltepunkts in visual Studio für mac](media/unity-image25.png)

2. Klicken Sie auf die **Debuggen starten** Schaltfläche oder drücken Sie die **F5**. Das Projekt erstellen wird und für das Debuggen an Unity anfügen.

    ![Schaltfläche "Start" in visual Studio für mac](media/unity-image26.png)

3. Wechseln Sie zurück zur **Unity** , und klicken Sie auf die **ausführen** Schaltfläche, um das Spiel zu starten.

    ![Schaltfläche "ausführen" in unity](media/unity-image27.png)

4. Der Haltepunkt erreicht werden, und jetzt können Sie die Visual Studio für Mac-debugging-Tools.

    ![Haltepunkt erreicht, die in visual Studio für mac](media/unity-image28.png)

5. Von der **"lokal"** auffüllen, suchen Sie nach der **dies** Zeiger, der verweist auf eine **"enemyai"** Objekt. Erweitern Sie den Verweis, und sehen, dass Sie die zugehörigen Elemente wie das Durchsuchen **Geschwindigkeit**.

    ![lokal Debuggen Pad in visual Studio für mac](media/unity-image29.png)

6. Entfernen Sie den Haltepunkt aus der **starten** Methode die gleiche Weise, wie es war hinzugefügt – entweder durch Klicken sie auf den Rand oder auswählen, die Zeile, und drücken Sie **F9**.

    ![Haltepunkt erreicht, die in visual Studio für mac](media/unity-image30.png)

7. Drücken Sie **F10** zum Überspringen der ersten Zeile des Codes, die findet die **Player** spielobjekt mit einem Tag als Parameter.

8. Zeigen Sie den Mauszeiger auf die **Player** Variablen innerhalb der Code-Editor-Fenster, um deren zugehörigen Member anzuzeigen. Sie können auch die Überlagerung zum Anzeigen der untergeordneten Eigenschaften erweitern.

    ![Debugging-Fenster in visual Studio für Mac-editor](media/unity-image31.png)

9. Drücken Sie die **F5** , oder drücken Sie die **ausführen** Schaltfläche, um die Ausführung fortzusetzen. Zurück zu Unity gegnerischen Cube wiederholt den Player-Cube Ansatz finden Sie unter. Möglicherweise müssen Sie die Kamera anpassen, wenn es nicht angezeigt wird.

    ![das in Unity übernimmt Szene](media/unity-image32.png)

10. Wechseln Sie zurück zum **Visual Studio für Mac** und Festlegen eines Haltepunkts in der ersten Zeile von der **Update** Methode. Sie sollten sofort erreicht werden.

    ![Festlegen eines Haltepunkts in visual Studio für mac](media/unity-image33.png)

11. Nehmen Sie an die Geschwindigkeit ist nicht so schnell, und die Auswirkungen der Änderung zu testen, ohne die app wird neu gestartet werden soll. Suchen Sie die **Geschwindigkeit** Variablen innerhalb der **"Auto"** oder **"lokal"** Fenster und ändern Sie ihn in **"10"** , und drücken Sie **EINGABETASTE** .

    ![Anpassen von Variablen im Fenster "lokal"](media/unity-image34.png)

12. Entfernen Sie den Haltepunkt, und drücken Sie **F5** um die Ausführung fortzusetzen.

13. Wechseln Sie zurück zur **Unity** um die ausgeführte Anwendung anzuzeigen. Gegnerische Cube ist nun auf eine fünfte von der ursprünglichen Geschwindigkeit verschieben.

    ![Unity-Fenster mit der Ausführung der Anwendung](media/unity-image35.png)

14. Beenden Sie den Unity-app durch Klicken auf die **spielen** erneut.

    ![das Beenden der Unity-app](media/unity-image36.png)

15. Wechseln Sie zurück zur **Visual Studio für Mac**. Die Debugsitzung zu beenden, indem Sie auf die **beenden** Schaltfläche.

    ![Beenden die Debugsitzung in Visual Studio für Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Aufgabe 4: Erkunden Unity-Funktionen in Visual Studio für Mac

1. Visual Studio für Mac bietet schnellen Zugriff auf die Unity-Dokumentation im Code-Editor. Platzieren Sie den Cursor an einer beliebigen Stelle auf der **Vector3** symbol in der **Update** -Methode, und drücken Sie **⌘ Befehl + '** .

    ![Auswählen der Methode in visual Studio für Mac-editor](media/unity-image38.png)

2. Ein neues Browserfenster wird geöffnet, in der Dokumentation zu **Vector3**. Schließen Sie das Browserfenster, wenn erfüllt.

    ![Browserfenster wird geöffnet, in der Dokumentation](media/unity-image39.png)

3. Visual Studio für Mac bietet auch einige Hilfsmethoden aus, um schnell Unity Verhaltensklassen erstellen. Von **Projektmappen-Explorer**, mit der rechten Maustaste **Assets** , und wählen Sie **hinzufügen > New MonoBehaviour**.

    ![Neues Monobehaviour-kontextaktion](media/unity-image40.png)

4. Die neu erstellte Klasse bietet Stubs für die **starten** und **Update** Methoden. Nach der schließenden Klammer des der **Update** -Methode, mit der Eingabe beginnen **"Onmouseup"** . Beachten Sie, dass es sich bei Visual Studio IntelliSense schnell auf die Methode Nullen, die Sie implementieren möchten, während der Eingabe. Wählen sie aus der angegebenen AutoVervollständigen-Liste. Es wird ein Methodenstub für Sie, einschließlich aller Parameter ausfüllen.

    ![IntelliSense in visual Studio für mac](media/unity-image41.png)

5. In der **OnMouseUp** -Methode, Typ **"base".** Um alle Basismethoden aufrufen zur Verfügung. Sie können auch die anderen Überladungen für jede Funktion, die mit der Auslagerung-Option in der oberen rechten Ecke des Flyouts IntelliSense durchsuchen.

    ![Untersuchen von Überladungen in für visual Studio für mac](media/unity-image42.png)

6. Visual Studio für Mac können auch Sie problemlos neue Shader definieren. Von **Projektmappen-Explorer**, mit der rechten Maustaste **Assets** , und wählen Sie **hinzufügen > neuer Shader**.

    ![neue Shader-Aktion in visual Studio für mac](media/unity-image43.png)

7. Das Shader-Dateiformat ruft vollständige Farbe und Schriftart behandelt, um ihn leichter zu lesen und zu verstehen.

    ![Syntaxhervorhebung](media/unity-image44.png)

8. Wechseln Sie zurück zur **Unity**. Sie sehen, da Visual Studio für Mac mit dem gleichen Projektsystem arbeitet, Änderungen, die in keinem dieser Ordner automatisch mit den anderen synchronisiert werden. Jetzt ist es einfach, immer das beste Tool für den Task zu verwenden.

    ![Unity-objektepanel](media/unity-image45.png)

## <a name="summary"></a>Zusammenfassung

In dieser Übungseinheit haben Sie gelernt, wie Sie beginnen, erstellen ein Spiel mit Unity und Visual Studio für Mac. Finden Sie unter [ https://unity3d.com/learn ](https://unity3d.com/learn) Weitere Informationen zu Unity.
