# Unityにて利用


## Actor Class


```
using System;
using UnityEngine;
using System.IO;

namespace ActorData
{

    public class ActorClass
    {
        public Actor[] actors;
    }

    [System.Serializable]
    public class Actor
    {
        public string actor_id;
        public string gamegameObjectName;
        public Actor_Name actor_name;
        public Actor_Images actor_images;
        public Actor_Musics actor_musics;
        public Actor_Voices actor_voices;
        public Position position;
    }

    [System.Serializable]
    public class Actor_Name
    {
        public Name_En name_en;
        public Name_Ja name_ja;
    }

    [System.Serializable]
    public class Name_En
    {
        public string name_full;
        public string name_first;
        public string name_last;
    }

    [System.Serializable]
    public class Name_Ja
    {
        public string name_full;
        public string name_full_furigana;
        public string name_first;
        public string name_first_furigana;
        public string name_last;
        public string name_last_furigana;
    }

    [System.Serializable]
    public class Actor_Images
    {
        public string tachie1;
        public string tachie2;
    }

    [System.Serializable]
    public class Actor_Musics
    {
        public string _default;
    }

    [System.Serializable]
    public class Actor_Voices
    {
        public string ohayou;
    }

    [System.Serializable]
    public class Position
    {
        public int x;
        public int y;
        public int z;
    }

}
```

## Actorを読み込み

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System.IO;
using ActorData;

public class GameController : MonoBehaviour
{
    public string json_nogatari_actors;
    public string json_nogatari_main;
    // Start is called before the first frame update

    void Start()
    {
        loadSenarioActor(json_nogatari_actors);
    }
    
    void loadSenarioActor(string json_nogatari_actors)
    {
        Debug.Log(json_nogatari_actors);
        var jsonString = File.ReadAllText(json_nogatari_actors);
        Debug.Log(jsonString);
        var thisObject = JsonUtility.FromJson<ActorClass>("{\"actors\":" + jsonString.ToString() + "}");
        Debug.Log(thisObject);
        for (var i = 0; i <= thisObject.actors.Length - 1; i++)
        {
            Debug.Log(i);
            Debug.Log(thisObject.actors[i].actor_id);
            Debug.Log(thisObject.actors[i].actor_name.name_ja.name_full);
            Debug.Log(thisObject.actors[i].actor_images);
            Debug.Log(thisObject.actors[i].actor_musics);
            Debug.Log(thisObject.actors[i].actor_voices);
            Debug.Log(thisObject.actors[i].position.x);
            Debug.Log(thisObject.actors[i].position.y);
            Debug.Log(thisObject.actors[i].position.z);
            GameObject thisGameObject = GameObject.Find(thisObject.actors[i].gamegameObjectName);
            thisGameObject.transform.position = new Vector3(thisObject.actors[i].position.x, thisObject.actors[i].position.y, thisObject.actors[i].position.z);
        }
    }
}

```
