---
title: Erstellen von Apps mit nativer Benutzeroberfläche über Xamarin in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 31
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 0ec6529e6a9c41d1b9a4fa99a79d756754df1f45
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Erstellen von Apps mit systemeigener Benutzeroberfläche über Xamarin in Visual Studio

Die meisten Entwickler, die sich für Xamarin und C# zum Schreiben von plattformübergreifenden mobilen Anwendungen entscheiden, verwenden Xamarin.Forms. Xamarin.Forms definiert eine Benutzeroberfläche, die nativen Steuerelementen in iOS, Android und der universelle Windows-Plattform (UWP) zugeordnet wird. Xamarin.Forms wird im Artikel [Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) beschrieben.

In diesem Artikel wird ein anderer Ansatz erläutert, der den Zugriff auf die nativen Benutzeroberflächen-APIs jeder Plattform beinhaltet. Die Arbeit mit nativen APIs ist ein viel schwierigerer Ansatz als bei Xamarin.Forms, da dies umfangreiche Kenntnisse der einzelnen Plattformen erfordert. Der Vorteil ist, dass Sie die Benutzeroberfläche an die besonderen Stärken und Fähigkeiten jeder Plattform anpassen können, während Sie gleichzeitig die zugrunde liegende Geschäftslogik teilen.

Nachdem Sie die Schritte unter [Setup und Installation](../cross-platform/setup-and-install.md) und [Überprüfen Ihrer Xamarin-Umgebung](../cross-platform/verify-your-xamarin-environment.md) ausgeführt haben, zeigt Ihnen diese exemplarische Vorgehensweise das Erstellen einer einfachen Xamarin-App mit nativen Benutzeroberflächenebenen. Bei nativen Benutzeroberflächen befindet sich der freigegebene Code in einer .NET Standard-Bibliothek, und die einzelnen Plattformprojekte enthalten die UI-Definitionen. Hier ist die Anwendung, die Sie auf (von links nach rechts) iOS- und Android-Smartphones und dem Windows 10-Desktop erstellen werden.
  
[![Xamarin-App unter iOS, Android und Windows](../cross-platform/media/cross-plat-xamarin-build-1.png "Plattformübergreifende Xamarin-Entwicklung 1")](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)
  
Zum Erstellen müssen Sie die folgenden Schritte ausführen:  
  
- [Einrichten der Projektmappe](#solution)  
  
- [Schreiben von freigegebenem Datendienstcode](#dataservice)  
  
- [Entwickeln der Benutzeroberfläche für Android](#Android)  

- [Entwickeln der Benutzeroberfläche für Windows](#Windows)  
  
- [Nächste Schritte](#next), in denen auch eine Benutzeroberfläche für iOS entworfen wird.
  
> [!TIP]
> Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „Mobile Samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Wenn Sie Probleme haben oder Fehler auftreten, posten Sie Ihre Fragen bitte auf [forums.xamarin.com](http://forums.xamarin.com). Viele Fehler können behoben werden, indem ein Update auf die neuesten von Xamarin erforderlichen SDKs durchgeführt wird. Diese werden unter [Xamarin Release Notes](https://developer.xamarin.com/releases/) (Xamarin-Versionshinweise) für die einzelnen Plattformen beschrieben.    
  
> [!NOTE]
> Die Xamarin-Entwicklerdokumentation bietet außerdem, wie nachstehend aufgelistet, eine Reihe von exemplarischen Vorgehensweisen mit Schnellstart- und vertiefenden Abschnitten. Achten Sie für jede dieser Seiten darauf, dass „Visual Studio“ ausgewählt ist, damit Visual Studio-spezifische exemplarische Vorgehensweisen angezeigt werden.  
>   
>  -   Xamarin-Apps mit systemeigener Benutzeroberfläche:  
>     -   [Hello, Android](/xamarin/android/get-started/hello-android/) (einfache App mit einem Bildschirm)  
>     -   [Hello, Android multiscreen](/xamarin/android/get-started/hello-android-multiscreen/) (App mit Navigation zwischen Bildschirmen)  
>     -   [Android Fragments Walkthrough](/xamarin/android/platform/fragments/fragments/implementing-with-fragments/walkthrough/) (u. a. für die Demonstration von Haupt-/Detailbildschirmen verwendet)  
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)  
>     -   [Hello, iOS Multiscreen](/xamarin/ios/get-started/hello-iOS-multiscreen/) 

>  -   Xamarin-Apps mit Xamarin.Forms (gemeinsame Benutzeroberfläche)  
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)  
>     -   [Hello, Xamarin.Forms Multiscreen](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)  
  
<a name="solution" />

##  <a name="set-up-your-solution"></a>Einrichten der Projektmappe  

Visual Studio verfügt nicht über eine Projektmappenvorlage zum Erstellen von Anwendungen für native Benutzeroberflächen, die eine gemeinsame .NET Standard-Bibliothek nutzen. Es ist jedoch nicht schwer, eine solche Projektmappe aus den einzelnen Projekten zu erstellen. Mit diesen Schritten erstellen Sie eine Xamarin-Projektmappe mit Projekten für jeden Anwendungsplattformtyp und eine .NET Standard-Bibliothek für freigegebenen Code.  
  
1.  Erstellen Sie in Visual Studio eine neue Projektmappe **Klassenbibliothek (.NET Standard)**, und nennen Sie diese **WeatherApp**. Am einfachsten finden Sie diese Vorlage, indem Sie links **Visual C#** und dann **.NET Standard** auswählen: 

    ![Erstellen der Projektmappe für .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png "Plattformübergreifende Xamarin-Entwicklung 2")

    Nachdem Sie auf „OK“ geklickt haben, besteht die Projektmappe **WeatherApp** aus einem einzelnen Projekt namens **WeatherApp**. 

2.  Wenn Sie auf iOS abzielen, fügen Sie ein iOS-Projekt zur Projektmappe hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektmappennamen, und wählen Sie **Hinzufügen** und **Neues Projekt**.  Wählen Sie links im Dialogfeld **Neues Projekt** die Optionen **Visual C#** und dann **iOS** und **Universell**. (Wenn Sie sie dort nicht finden, müssen Sie möglicherweise Xamarin installieren oder das Visual Studio 2017-Feature aktivieren, wie unter [Setup und Installation](../cross-platform/setup-and-install.md) beschrieben.) Wählen Sie in der Vorlagenliste **Einzelansicht-App (iOS)** aus. Nennen Sie sie **WeatherApp.iOS**.

3.  Wenn Sie auf Android abzielen, fügen Sie ein Android-Projekt zur Projektmappe hinzu. Wählen Sie links im Dialogfeld **Neues Projekt** die Option **Visual C#** und dann **Android**. Wählen Sie in der Vorlagenliste **Leere App (Android)** aus. Nennen Sie sie **WeatherApp.Android**. 

4. Wenn Sie auf die universelle Windows-Plattform abzielen, wählen Sie links im Dialogfeld **Neues Projekt** die Optionen **Visual C#**, und **Universelles Windows** aus. Wählen Sie in der Vorlagenliste **Leere App (universelles Windows)**, und nennen Sie sie **WeatherApp.UWP**.
  
5. Klicken Sie für jedes der Anwendungsprojekte (iOS, Android und UWP) mit der rechten Maustaste im **Projektmappen-Explorer** auf den Abschnitt **Verweise**, und wählen Sie **Verweis hinzufügen**. Wählen Sie links im Dialogfeld **Verweis-Manager** die Optionen **Projekt** und **Projektmappe**. Im Projektmappen-Explorer sehen Sie eine Liste aller Projekte, mit Ausnahme des Projekts, dessen Verweise Sie gerade verwalten:

   ![Festlegen eines Verweises auf das .NET Standard-Projekt](../cross-platform/media/cross-plat-xamarin-build-3.png "Plattformübergreifende Xamarin-Entwicklung 3")

   Aktivieren Sie das Kontrollkästchen neben **WeatherApp**. 

   Nachdem Sie dieses Kontrollkästchen für jedes der Anwendungsprojekte aktiviert haben, enthalten alle Projekte Verweise auf die .NET Standard-Bibliothek und können den Code in dieser Bibliothek nutzen.
  
6. Fügen Sie das NuGet-Paket **Newtonsoft.Json** zum .NET Standard-Projekt hinzu, das Sie zum Verarbeiten der von einem Wetterdatendienst abgerufenen Informationen verwenden:  
  
    -   Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **WeatherApp**, und wählen Sie **NuGet-Pakete verwalten...** aus.  
  
         Wählen Sie im NuGet-Fenster die Registerkarte **Durchsuchen** aus, und suchen Sie nach **Newtonsoft**.  
  
    -   Wählen Sie **Newtonsoft.Json**aus.  
  
    -   Stellen Sie sicher, dass das **Version** -Feld auf die **neueste stabile** Version festgelegt ist.  
  
    -   Klicken Sie auf **Installieren**.  
  
7.  Wiederholen Sie Schritt 7, um das **Microsoft.CSharp**-Paket im .NET Standard-Projekt zu suchen und zu installieren. Diese Bibliothek wird benötigt, um den C#-`dynamic`-Datentyp in einer .NET Standard-Bibliothek zu verwenden.
  
8.  Erstellen Sie die Projektmappe, und vergewissern Sie sich, dass keine Buildfehler aufgetreten sind.  
  
<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Schreiben von freigegebenem Datendienstcode  

 Das **WeatherApp**-Projekt ist die .NET Standard-Bibliothek. In diesem Projekt werden Sie Code schreiben, der auf allen Plattformen gemeinsam genutzt wird. Da jedes Anwendungsprojekt einen Verweis auf die .NET Standard-Bibliothek hat, ist die Bibliothek in den App-Paketen von iOS, Android und UWP enthalten.  
  
 Mit den folgenden Schritten fügen Sie Code zu der .NET Standard-Bibliothek hinzu, um auf Daten dieses Wetterdiensts zuzugreifen und diese zu speichern:  
  
1.  Registrieren Sie sich zuerst für einen kostenlosen Wetter-API-Schlüssel unter [http://openweathermap.org/appid](http://openweathermap.org/appid). Dieser API-Schlüssel ermöglicht es der Anwendung, das Wetter für jede Postleitzahl der Vereinigten Staaten abzurufen. (Es funktioniert nicht für Postleitzahlen außerhalb der USA.)
  
2.  Klicken Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt, und wählen Sie **Hinzufügen > Klasse…** aus. Geben Sie der Datei im Dialogfeld **Neues Element hinzufügen** den Namen **Weather.cs**. Sie nutzen diese Klasse später, um Daten aus dem Wetterdatendienst zu speichern.  
  
3.  Ersetzen Sie den gesamten Inhalt von **Weather.cs** durch folgenden Code:  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
4.  Fügen Sie eine weitere Klasse zum .NET Standard-Projekt mit dem Namen **DataService.cs** hinzu. Sie nutzen diese Klasse später, um JSON-Daten aus dem Wetterdatendienst zu verarbeiten.  
  
5.  Ersetzen Sie den gesamten Inhalt von **DataService.cs** durch folgenden Code:  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
  
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
6.  Fügen Sie der .NET Standard-Bibliothek eine dritte Klasse namens **Core.cs** hinzu. Sie verwenden diese Klasse, um eine Abfragezeichenfolge mit einer Postleitzahl zu bilden, den Wetterdatendienst aufzurufen und eine Instanz der Klasse **Weather** zu füllen.  
  
7.  Ersetzen Sie den Inhalt von **Core.cs** durch folgenden Code:  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR API KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
8. Ersetzen Sie das erste Vorkommen von *YOUR API KEY HERE* durch den in Schritt 1 erhaltenen API-Schlüssel. Er muss noch in Anführungszeichen stehen.
  
9. Löschen Sie **MyClass.cs** in der .NET Standard-Bibliothek, da Sie diese nicht benötigen.  
  
10. Erstellen Sie das Projekt **WeatherApp**, um sicherzustellen, dass der Code korrekt ist.  
  
<a name="Android" />

## <a name="design-ui-for-android"></a>Entwickeln der Benutzeroberfläche für Android  

 Sie können nun die Benutzeroberfläche entwickeln, diese mit dem freigegebenen Code verbinden und dann die App ausführen.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Entwickeln des Erscheinungsbilds und Verhaltens der App  
  
1.  Erweitern Sie im **Projektmappen-Explorer** den Ordner **WeatherApp.Droid > Ressourcen > Layout**, und öffnen Sie **Main.axml**. Über diesen Befehl wird die Datei im visuellen Designer geöffnet. (Wenn ein Java-bezogener Fehler angezeigt wird, lesen Sie diesen [Blogbeitrag](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)  
  
    > [!TIP]
    >  Es sind viele weitere Dateien in diesem Projekt vorhanden. Sie alle zu besprechen, würde den Rahmen dieses Artikels sprengen. Wenn Sie jedoch mehr über die Struktur eines Android-Projekts erfahren möchten, finden Sie ausführliche Informationen im Artikel „Hello Android“ unter [Part 2 Deep Dive (Detailinformationen, Teil 2)](/xamarin/android/get-started/hello-android/hello-android-deepdive/).  
  
2.  Öffnen Sie die Toolbox mit **Ansicht > Andere Fenster > Toolbox**.  
  
3.  Ziehen Sie aus dem **Werkzeugkasten**ein **RelativeLayout** -Steuerelement in den Designer. Sie werden dieses Steuerelement als übergeordneten Container für andere Steuerelemente verwenden.  
  
    > [!TIP]
    >  Wenn das Layout zu einem beliebigen Zeitpunkt noch nicht richtig angezeigt zu werden scheint, speichern Sie die Datei. Wechseln Sie dann zwischen den Registerkarten **Design** und **Quelle**, um eine Aktualisierung durchzuführen.  
  
4.  Setzen Sie im Fenster **Eigenschaften** die Eigenschaft **Hintergrund** (in der Formatvorlagengruppe) auf `#545454`.  Stellen Sie durch die Überschrift im Fenster **Eigenschaften** sicher, dass Sie den Hintergrund für das **RelativeLayout** einstellen.
  
5.  Ziehen Sie aus dem **Werkzeugkasten**ein **TextView** -Steuerelement auf das **RelativeLayout** -Steuerelement.  
  
6.  Legen Sie im Fenster **Eigenschaften** diese Eigenschaften fest. (Es kann helfen, die Liste mithilfe der Sortierschaltfläche in der Symbolleiste des Fensters „Eigenschaften“ alphabetisch zu sortieren):  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**text**|**Search by Zip Code**|  
    |**ID**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  Beachten Sie, dass viele Eigenschaften nicht über eine Dropdownliste mit Werten verfügen, die Sie auswählen können.  Es kann schwierig sein, zu raten, welcher Zeichenfolgenwert für eine bestimmte Eigenschaft verwendet werden soll. Vorschläge können Sie möglicherweise erhalten, indem Sie auf der Seite der Klasse [R.attr](http://developer.android.com/reference/android/R.attr.html) nach dem Namen einer Eigenschaft suchen.  
    >   
    >  Eine schnelle Websuche führt Sie außerdem meist zu einer Seite auf [http://stackoverflow.com/](http://stackoverflow.com/), wo Sie sich mit anderen austauschen können, die bereits die gleiche Eigenschaft verwendet haben.  
  
     Wenn Sie zur Ansicht **Quelle** wechseln, sollten Sie den folgenden Code für dieses Element als Referenz sehen:  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_marginStart="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
7.  Ziehen Sie aus der **Toolbox** ein **TextView**-Steuerelement auf das Steuerelement **RelativeLayout**, und positionieren Sie es unter dem Steuerelement „ZipCodeSearchLabel“. Legen Sie das neue Steuerelement auf den entsprechenden Rand des vorhandenen Steuerelements. Es hilft, die Designeransicht etwas zu vergrößern, um das Steuerelement zu positionieren.  
  
8. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Text**|**Zip Code**|  
    |**ID**|`@+id/ZipCodeLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginTop**|`6dp`|  
    |**textColor**|`@android:color/white`|  
  
    Der Code in der Ansicht **Quelle** sollte wie folgt aussehen:  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"  
        android:textColor="@android:color/white" />  
    ```  
  
9. Ziehen Sie aus der **Toolbox** ein **Number**-Steuerelement auf **RelativeLayout**, und positionieren Sie es unter der Beschriftung **Zip Code**. Legen Sie dann die folgenden Eigenschaften fest:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**ID**|`@+id/zipCodeEntry`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
    |**textColor**|`@android:color/white`|  
  
    In das Steuerelement **Anzahl** gibt der Benutzer eine fünfstellige Postleitzahl in den USA ein. Hier sehen Sie das entsprechende Markup zu diesem Steuerelement:  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginStart="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp"  
        android:textColor="@android:color/white" />  
    ```  
  
10. Ziehen Sie aus der **Toolbox** eine **Schaltfläche** auf das Steuerelement **RelativeLayout**, und positionieren Sie sie rechts neben dem Steuerelement „zipCodeEntry“. Legen Sie dann diese Eigenschaften fest:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**ID**|`@+id/weatherBtn`|  
    |**Text**|**Get Weather**|  
    |**layout_marginStart**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button
        android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginStart="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
11. Sie verfügen jetzt über ausreichende Kenntnisse, um eine einfache Benutzeroberfläche mit dem Android-Designer zu erstellen. Sie können zudem eine Benutzeroberfläche erstellen, indem Sie Markup direkt zur Main.asxml-Datei auf der Seite hinzufügen. Um den Rest der Benutzeroberfläche auf diese Weise zu erstellen, wechseln Sie im Designer in die Quellansicht, und fügen Sie dann das folgende Markup *unter* dem `</RelativeLayout>`-Endtag ein. (Sie müssen sich unter dem Tag befinden, da diese Elemente *nicht* im `RelativeLayout` enthalten sind.)  
  
    ```xml  
    <TextView  
        android:text="Location"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationLabel"  
        android:layout_marginStart="10dp"  
        android:layout_marginTop="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationText"  
        android:layout_marginStart="20dp"  
        android:layout_marginBottom="10dp" />  
    <TextView  
        android:text="Temperature"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Wind Speed"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Humidity"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidtyLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Visibility"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunrise"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunset"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    ```  
  
12. Speichern Sie die Datei, und wechseln Sie zur Ansicht **Design**. Die Benutzeroberfläche sollte folgendermaßen aussehen:  
  
     ![Benutzeroberfläche für Android-App](../cross-platform/media/xamarin_androidui.png "Xamarin_AndroidUI")  
  
13. Öffnen Sie **MainActivity.cs**. Der Code sollte wie folgt aussehen:  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
14. Erstellen Sie das Android-Projekt, um Ihre Arbeit zu überprüfen. Beim Erstellungsprozess werden der Datei **Resource.Designer.cs** Steuerelement-IDs hinzugefügt, sodass Sie im Code mit Namen auf die Steuerelemente verweisen können.  
  
### <a name="consume-your-shared-code"></a>Verwenden des freigegebenen Codes  
  
1.  Öffnen Sie die Datei **MainActivity.cs** des Projekts **WeatherApp** im Code-Editor, und ersetzen Sie seinen Inhalt durch den unten stehenden Code. Dieser Code ruft die `GetWeather` -Methode auf, die Sie im freigegebenen Code definiert haben. Dann werden auf der Benutzeroberfläche der App die Daten angezeigt, die durch diese Methode abgerufen werden.  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", 
                  Theme = "@android:style/Theme.Material.Light", 
                  MainLauncher = true)]  
        public class MainActivity : Activity  
        {  
            protected override void OnCreate(Bundle bundle)  
            {  
                base.OnCreate(bundle);  
  
                SetContentView(Resource.Layout.Main);  
  
                Button button = FindViewById<Button>(Resource.Id.weatherBtn);  
  
                button.Click += Button_Click;  
            }  
  
            private async void Button_Click(object sender, EventArgs e)  
            {  
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);  
  
                if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
                {  
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;  
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;  
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;  
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;  
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;  
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;  
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;  
                }  
            }  
        }  
    }  
    ```  

    Beachten Sie, dass der Aktivität ein Design für einen hellen Hintergrund zugewiesen wurde.
  
### <a name="run-the-app-and-see-how-it-looks"></a>Ausführen der App und Prüfen der Anzeige  
  
1.  Stellen Sie im **Projektmappen-Explorer** sicher, dass das Projekt **WeatherApp.Droid** als Startprojekt festgelegt ist.  
  
2.  Wählen Sie ein geeignetes Gerät oder Emulatorziel, und starten Sie die App durch Drücken der Taste F5.  

    > [!NOTE]
    > Wenn Visual Studio anzeigt, dass das Android-Projekt die Datei „Newtonsoft.Json“ nicht finden kann, fügen Sie das NuGet-Paket zum Android-Projekt hinzu. 
  
3.  Geben Sie auf dem Gerät oder im Emulator eine gültige fünfstellige Postleitzahl für die USA in das Bearbeitungsfeld ein, und drücken Sie dann **Get Weather** (Wetter abrufen). In den Steuerelementen werden nun Wetterdaten für diese Region angezeigt.  
  
    [![Xamarin-App unter Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png "Plattformübergreifende Xamarin-Entwicklung 1 – Android")](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)  
  
> [!TIP]
>  Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
<a name="Windows" /> 

## <a name="design-ui-for-windows"></a>Entwickeln der Benutzeroberfläche für Windows

Im nächsten Schritt entwickeln Sie die Benutzeroberfläche für Windows, verbinden sie mit Ihrem freigegebenen Code und führen dann die App aus.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Entwickeln des Erscheinungsbilds und Verhaltens der App  

 Das Entwickeln einer nativen UWP-Benutzeroberfläche in einer Xamarin-App unterscheidet sich nicht von anderen nativen UWP-Apps. Aus diesem Grund wird hier nicht auf den Einsatz des Designers eingegangen. Weitere Informationen finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer in Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 Öffnen Sie stattdessen **MainPage.xaml**, und ersetzen Sie den gesamten XAML-Inhalt durch das folgende Markup:   
  
```xaml  
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="120" Margin="10,40,0,0" Width="400" 
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap" 
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />
            
            <TextBlock Text="Zip Code" TextWrapping="Wrap" 
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            
            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text="" 
                         Margin="10,10,0,0" VerticalAlignment="Top" 
                         InputScope="Number" Width="165" />
                
                <Button x:Name="weatherBtn" Content="Get Weather" 
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60" 
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        
        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>
                
                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>
            
            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```  
  
### <a name="consume-your-shared-code"></a>Verwenden des freigegebenen Codes  
  
Fügen Sie in der CodeBehind-Datei **MainPage.xaml.cs** den folgenden Ereignishandler für die Schaltfläche hinzu: 
  
```csharp  
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)  
{  
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
    {  
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
        locationText.Text = weather.Title;  
        tempText.Text = weather.Temperature;  
        windText.Text = weather.Wind;  
        visibilityText.Text = weather.Visibility;  
        humidityText.Text = weather.Humidity;  
        sunriseText.Text = weather.Sunrise;  
        sunsetText.Text = weather.Sunset;  

        weatherBtn.Content = "Search Again";  
    }  
}  
```  
  
Dieser Code ruft die `GetWeather` -Methode auf, die Sie im freigegebenen Code definiert haben. Es handelt sich bei `GetWeather` um die gleiche Methode, die Sie in der Android-App aufgerufen haben. Dieser Code zeigt ebenfalls Daten, die mit dieser Methode aus den Steuerelementen der Benutzeroberfläche der App gewonnen wurden.  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Ausführen der App und Prüfen der Anzeige  
  
1.  Legen Sie im **Projektmappen-Explorer** das Projekt **WeatherApp.UWP** als Startprojekt fest.  

2.  Wählen Sie im Dropdownfeld **Projektmappenplattformen** die Option **x86**, und wählen Sie **Lokaler Computer**, um die Anwendung auf dem Windows 10-Desktop bereitzustellen.
  
3.  Starten Sie die App durch Drücken der Taste "F5".  
  
4.  Geben Sie in das Bearbeitungsfeld die fünfstellige Postleitzahl aus den USA ein, und drücken Sie **Get Weather** (Wetter abrufen). Auf der Seite werden nun Wetterdaten für diese Region angezeigt.  

    [![Xamarin-App unter UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png "Plattformübergreifende Xamarin-Entwicklung 1 – UWP")](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)  

> [!TIP]
>  Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  

<a name="next" /> 

## <a name="next-steps"></a>Nächste Schritte  

 **Hinzufügen einer Benutzeroberfläche für iOS zum Projekt**  
  
 Erweitern Sie dieses Beispiel, indem Sie eine native Benutzeroberfläche für iOS hinzufügen. Zum Testen des Codes unter iOS müssen Sie über Ihr lokales Netzwerk eine Verbindung zu einem Mac herstellen, auf dem Xcode und Xamarin installiert sind. Anschließend können Sie den iOS-Designer direkt in Visual Studio verwenden. Weitere Informationen finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
 Beachten Sie auch die exemplarische Vorgehensweise für [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).   
  
 **Hinzufügen von plattformspezifischem Code in einem freigegebenen Projekt**  
  
 Freigegebener Code in einer .NET Standard-Bibliothek ist plattformunabhängig. Die Bibliothek wird einmalig kompiliert und ist in jedem plattformspezifischen App-Paket enthalten. Wenn Sie freigegebenen Code schreiben möchten, der eine bedingte Kompilierung verwendet, um plattformspezifischen Code zu isolieren, können Sie ein *freigegebenes* Projekt verwenden. Weitere Informationen finden Sie unter [Optionen für die Codefreigabe](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).  
  
## <a name="see-also"></a>Siehe auch  

 [Xamarin-Dokumentation](http://docs.microsoft.com/xamarin)   
 [Windows Dev Center](https://dev.windows.com/en-us)   
 [Schnellreferenzposter zu Swift und C#](http://aka.ms/scposter)