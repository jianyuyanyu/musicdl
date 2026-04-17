# Music Clients

This section explains how to use all music clients supported by musicdl, covering two main scenarios: direct use from the terminal and integration within Python code.

## Platforms in Greater China

#### BilibiliMusicClient

[Bilibili Music](https://www.bilibili.com/audio/home/?type=9) is Bilibili’s dedicated audio platform, where users can discover, stream, and enjoy a wide variety of music, podcasts, and original audio content.

We can use BilibiliMusicClient to download music from the above music platform.

BilibiliMusicClient requires no additional CLI tools such as ffmpeg or N_m3u8DL-RE. Just install musicdl via pip and it is ready to use out of the box.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m BilibiliMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m BilibiliMusicClient -i "{'BilibiliMusicClient': {'default_search_cookies': 'YOUR_COOKIES', 'default_download_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['BilibiliMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'BilibiliMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
        'default_download_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['BilibiliMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

#### FiveSingMusicClient

[5SING Music](https://5sing.kugou.com/index.html) is a KuGou-affiliated online music platform where users can upload and discover original songs, covers, instrumentals, playlists, videos, and independent musicians.

FiveSingMusicClient can be used to download music from the music platform mentioned above.

Using FiveSingMusicClient does not require installing any extra command-line tools like ffmpeg or N_m3u8DL-RE. Simply run pip install musicdl and you can start using it right away.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m FiveSingMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m FiveSingMusicClient -i "{'FiveSingMusicClient': {'default_search_cookies': 'YOUR_COOKIES', 'default_download_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://5sing.kugou.com/yeluoluo/dj/631b3fa72418b11003089b8d.html" -m FiveSingMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:
  
  `musicdl -p "https://5sing.kugou.com/yeluoluo/dj/631b3fa72418b11003089b8d.html" -m FiveSingMusicClient -i "{'FiveSingMusicClient': {'default_parse_cookies': 'YOUR_COOKIES', 'default_download_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['FiveSingMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'FiveSingMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
        'default_download_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['FiveSingMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['FiveSingMusicClient'])
  song_infos = music_client.parseplaylist("https://5sing.kugou.com/yeluoluo/dj/631b3fa72418b11003089b8d.html")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'FiveSingMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
        'default_download_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['FiveSingMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://5sing.kugou.com/yeluoluo/dj/631b3fa72418b11003089b8d.html")
  music_client.download(song_infos=song_infos)
  ```

#### KugouMusicClient (Built-in Premium Account)

[KuGou Music](http://www.kugou.com/) is a major Chinese online music platform that offers songs, charts, playlists, music videos, audiobooks, and live content.

Music from the above platform can be downloaded using KugouMusicClient.

KugouMusicClient works out of the box with no need for extra CLI dependencies such as ffmpeg or N_m3u8DL-RE — all you need is pip install musicdl.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m KugouMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  Kugou Music membership cookies copied directly from the web page can easily cause issues, so we provide the script [build_cookies_for_kugou.py](https://github.com/CharlesPikachu/musicdl/blob/master/scripts/build_cookies_for_kugou.py) in the repository to help you directly obtain valid cookies for your member account. 
  The output format is as follows:
  
  ```python
  {'KUGOU_API_GUID': 'xxx', 'KUGOU_API_MID': 'xxx', 'KUGOU_API_MAC': 'xxx', 'KUGOU_API_DEV': 'xxx', 'token': 'xxx', 'userid': 'xxx', 'dfid': 'xxx'}
  ```
  
  Then, you can use KugouMusicClient just like other music clients by passing the membership cookies as follows,
  
  `musicdl -m KugouMusicClient -i "{'KugouMusicClient': {'default_search_cookies': 'YOUR_COOKIES', 'default_download_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://www.kugou.com/yy/special/single/18170.html" -m KugouMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://www.kugou.com/yy/special/single/18170.html" -m KugouMusicClient -i "{'KugouMusicClient': {'default_parse_cookies': 'YOUR_COOKIES', 'default_download_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['KugouMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'KugouMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
        'default_download_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['KugouMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['KugouMusicClient'])
  song_infos = music_client.parseplaylist("https://www.kugou.com/yy/special/single/18170.html")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'KugouMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
        'default_download_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['KugouMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://www.kugou.com/yy/special/single/18170.html")
  music_client.download(song_infos=song_infos)
  ```

#### KuwoMusicClient (Built-in Premium Account)

[Kuwo Music](http://www.kuwo.cn/) is a major Chinese online music platform that offers high-quality music streaming, charts, playlists, radio, and downloadable songs.

We can download music from the aforementioned platform with KuwoMusicClient.

No additional command-line tools, including ffmpeg or N_m3u8DL-RE, are needed to use KuwoMusicClient. Installing musicdl with pip is enough to get started immediately.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m KuwoMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m KuwoMusicClient -i "{'KuwoMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://www.kuwo.cn/playlist_detail/2648040171" -m KuwoMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://www.kuwo.cn/playlist_detail/2648040171" -m KuwoMusicClient -i "{'KuwoMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['KuwoMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'KuwoMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['KuwoMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['KuwoMusicClient'])
  song_infos = music_client.parseplaylist("https://www.kuwo.cn/playlist_detail/2648040171")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'KuwoMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['KuwoMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://www.kuwo.cn/playlist_detail/2648040171")
  music_client.download(song_infos=song_infos)
  ```

#### MiguMusicClient

[Migu Music](https://music.migu.cn/v5/#/musicLibrary) is a Chinese music streaming platform that offers a large library of songs, albums, playlists, and other digital music content.

MiguMusicClient allows us to download music from the platform above.

MiguMusicClient can be used directly without installing any extra CLI utilities like ffmpeg or N_m3u8DL-RE. Just install musicdl via pip and it is good to go.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m MiguMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m MiguMusicClient -i "{'MiguMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://music.migu.cn/v5/#/playlist?playlistId=208219194&playlistType=create" -m MiguMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://music.migu.cn/v5/#/playlist?playlistId=208219194&playlistType=create" -m MiguMusicClient -i "{'MiguMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['MiguMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'MiguMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['MiguMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['MiguMusicClient'])
  song_infos = music_client.parseplaylist("https://music.migu.cn/v5/#/playlist?playlistId=208219194&playlistType=create")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'MiguMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['MiguMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://music.migu.cn/v5/#/playlist?playlistId=208219194&playlistType=create")
  music_client.download(song_infos=song_infos)
  ```

#### NeteaseMusicClient (Built-in Premium Account)

[NetEase Cloud Music](https://music.163.com/) is one of China’s most popular music streaming platforms, known for its vast song library, personalized recommendations, and active user community.

NeteaseMusicClient makes it possible to download music from the above platform.

There is no need to install extra tools such as ffmpeg or N_m3u8DL-RE to use NeteaseMusicClient. A simple pip install musicdl is all it takes.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m NeteaseMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m NeteaseMusicClient -i "{'NeteaseMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://music.163.com/#/my/m/music/playlist?id=7583298906" -m NeteaseMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://music.163.com/#/my/m/music/playlist?id=7583298906" -m NeteaseMusicClient -i "{'NeteaseMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['NeteaseMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'NeteaseMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['NeteaseMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['NeteaseMusicClient'])
  song_infos = music_client.parseplaylist("https://music.163.com/#/my/m/music/playlist?id=7583298906")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'NeteaseMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['NeteaseMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://music.163.com/#/my/m/music/playlist?id=7583298906")
  music_client.download(song_infos=song_infos)
  ```

#### QianqianMusicClient

[Qianqian Music](https://music.91q.com/) is an online music platform offering a large library of songs, popular playlists, artist content, and curated videos.

We use QianqianMusicClient to download music from the above-mentioned platform.

QianqianMusicClient comes ready to use without relying on additional CLI tools like ffmpeg or N_m3u8DL-RE. Just install musicdl through pip and you are all set.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m QianqianMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m QianqianMusicClient -i "{'QianqianMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://music.91q.com/songlist/309421" -m QianqianMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://music.91q.com/songlist/309421" -m QianqianMusicClient -i "{'QianqianMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['QianqianMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'QianqianMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['QianqianMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['QianqianMusicClient'])
  song_infos = music_client.parseplaylist("https://music.91q.com/songlist/309421")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'QianqianMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['QianqianMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://music.91q.com/songlist/309421")
  music_client.download(song_infos=song_infos)
  ```

#### QQMusicClient (Built-in Premium Account)

[QQ Music](https://y.qq.com/) is a high-quality music streaming platform offering a vast licensed song library, new releases, charts, playlists, MVs, and digital albums. 

QQMusicClient enables music downloads from the platform mentioned above.

To use QQMusicClient, you do not need any extra command-line tools such as ffmpeg or N_m3u8DL-RE. Once musicdl is installed with pip, it works immediately.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m QQMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m QQMusicClient -i "{'QQMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://y.qq.com/n/ryqq_v2/playlist/8740590963" -m QQMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://y.qq.com/n/ryqq_v2/playlist/8740590963" -m QQMusicClient -i "{'QQMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['QQMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'QQMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['QQMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['QQMusicClient'])
  song_infos = music_client.parseplaylist("https://y.qq.com/n/ryqq_v2/playlist/8740590963")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'QQMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['QQMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://y.qq.com/n/ryqq_v2/playlist/8740590963")
  music_client.download(song_infos=song_infos)
  ```

#### SodaMusicClient

[Soda Music](https://www.douyin.com/qishui/) is Douyin’s official music streaming app, designed to help users discover and enjoy personalized songs anytime, anywhere.

Music from the above-mentioned platform can be fetched using SodaMusicClient.

SodaMusicClient offers an out-of-the-box experience: no extra CLI tools like ffmpeg or N_m3u8DL-RE are required, and pip install musicdl is all you need.

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m SodaMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m SodaMusicClient -i "{'SodaMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://qishui.douyin.com/s/ix9JA2oW" -m SodaMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://qishui.douyin.com/s/ix9JA2oW" -m SodaMusicClient -i "{'SodaMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['SodaMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'SodaMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['SodaMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['SodaMusicClient'])
  song_infos = music_client.parseplaylist("https://qishui.douyin.com/s/ix9JA2oW")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'SodaMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['SodaMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://qishui.douyin.com/s/ix9JA2oW")
  music_client.download(song_infos=song_infos)
  ```

#### StreetVoiceMusicClient

[StreetVoice](https://www.streetvoice.cn/) is a music platform that helps independent artists share their work, reach new listeners, and grow through playlists, charts, discovery features, and a creator-focused community.

To download music from the platform above, we can use StreetVoiceMusicClient.

Since StreetVoice audio files are delivered in HLS format, downloading music from the platform with StreetVoiceMusicClient requires the command-line tool [FFmpeg](https://www.ffmpeg.org/).

(1) Command-Line Usage

- Basic usage for song search and download, without login cookies:

  `musicdl -m StreetVoiceMusicClient`

- Simple usage for searching and downloading songs, with login cookies:

  `musicdl -m StreetVoiceMusicClient -i "{'StreetVoiceMusicClient': {'default_search_cookies': 'YOUR_COOKIES'}}"`

- Basic usage for playlist parsing and downloading, without login cookies:

  `musicdl -p "https://www.streetvoice.cn/svmusic_cn/playlists/964546/" -m StreetVoiceMusicClient`

- Simple usage for playlist parsing and downloading, with login cookies:

  `musicdl -p "https://www.streetvoice.cn/svmusic_cn/playlists/964546/" -m StreetVoiceMusicClient -i "{'StreetVoiceMusicClient': {'default_parse_cookies': 'YOUR_COOKIES'}}"`

(2) Invoke It in Python

- Basic usage for song search and download, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['StreetVoiceMusicClient'])
  music_client.startcmdui()
  ```

- Simple usage for searching and downloading songs, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'StreetVoiceMusicClient': {
        'default_search_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['StreetVoiceMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  music_client.startcmdui()
  ```

- Basic usage for playlist parsing and downloading, without login cookies:

  ```python
  from musicdl import musicdl

  music_client = musicdl.MusicClient(music_sources=['StreetVoiceMusicClient'])
  song_infos = music_client.parseplaylist("https://www.streetvoice.cn/svmusic_cn/playlists/964546/")
  music_client.download(song_infos=song_infos)
  ```

- Simple usage for playlist parsing and downloading, with login cookies:

  ```python
  from musicdl import musicdl
  
  your_vip_cookies_with_str_or_dict_format = ''
  init_music_clients_cfg = {
    'StreetVoiceMusicClient': {
        'default_parse_cookies': your_vip_cookies_with_str_or_dict_format,
    }
  }
  music_client = musicdl.MusicClient(music_sources=['StreetVoiceMusicClient'], init_music_clients_cfg=init_music_clients_cfg)
  song_infos = music_client.parseplaylist("https://www.streetvoice.cn/svmusic_cn/playlists/964546/")
  music_client.download(song_infos=song_infos)
  ```

## Global Streaming / Indie

#### AppleMusicClient

#### DeezerMusicClient

#### JamendoMusicClient

JamendoMusicClient requires only a pip installation of musicdl, with no additional setup for tools like ffmpeg or N_m3u8DL-RE.

#### JooxMusicClient

With JooxMusicClient, there is no extra dependency on CLI tools such as ffmpeg or N_m3u8DL-RE. Just install musicdl and you are ready to go.

#### QobuzMusicClient

#### SoundCloudMusicClient

#### SpotifyMusicClient

#### TIDALMusicClient

#### YouTubeMusicClient


## Audio / Radio

#### LizhiMusicClient

LizhiMusicClient requires nothing beyond pip install musicdl — no extra CLI tools, no complicated setup.

#### LRTSMusicClient

You can start using LRTSMusicClient right after installing musicdl via pip, without having to install tools like ffmpeg or N_m3u8DL-RE.

#### QingtingMusicClient

QingtingMusicClient keeps things easy: no additional CLI tools to install, just pip install musicdl and you’re all set.

#### XimalayaMusicClient

XimalayaMusicClient is ready to use after a simple pip install. No extra command-line tools like ffmpeg or N_m3u8DL-RE are needed.


## Aggregators / Multi-Source Gateways

#### GDStudioMusicClient

There’s no need to set up extra CLI tools such as ffmpeg or N_m3u8DL-RE. Just install musicdl via pip and start using GDStudioMusicClient right away.

#### JBSouMusicClient

Using JBSouMusicClient is simple: just pip install musicdl. No additional tools like ffmpeg or N_m3u8DL-RE are required.

#### MP3JuiceMusicClient

MP3JuiceMusicClient doesn’t rely on external CLI tools like ffmpeg or N_m3u8DL-RE. Once you install musicdl, it’s ready to use.

#### MyFreeMP3MusicClient

No extra setup is needed for MyFreeMP3MusicClient — just install musicdl with pip and it will work out of the box.

#### TuneHubMusicClient

To use TuneHubMusicClient, all you need is pip install musicdl. You don’t have to install ffmpeg, N_m3u8DL-RE, or any other CLI tools.




## Unofficial Download Sites / Scrapers

#### BuguyyMusicClient

No extra CLI tools like ffmpeg or N_m3u8DL-RE are needed. Just run pip install musicdl and start using BuguyyMusicClient right away.



#### FangpiMusicClient

FangpiMusicClient works out of the box with just pip install musicdl — no ffmpeg, no N_m3u8DL-RE, and no other CLI tools required.

#### FiveSongMusicClient

Using FiveSongMusicClient does not require the installation of any additional command-line tools, such as ffmpeg or N_m3u8DL-RE. Installing musicdl via pip is sufficient for immediate use.

#### FLMP3MusicClient

Getting started with FLMP3MusicClient is easy: no need to install ffmpeg, N_m3u8DL-RE, or any other CLI tools. Just pip install musicdl and you are good to go.

#### GequbaoMusicClient

GequbaoMusicClient saves you from dealing with extra CLI dependencies like ffmpeg or N_m3u8DL-RE — a simple pip install musicdl is all it takes.

#### GequhaiMusicClient

GequhaiMusicClient is truly plug-and-play: no external CLI tools such as ffmpeg or N_m3u8DL-RE are required. Just install musicdl and use it instantly.

#### HTQYYMusicClient

There is no need to set up external command-line tools like ffmpeg or N_m3u8DL-RE when using HTQYYMusicClient. A single pip install musicdl is enough.

#### JCPOOMusicClient

To use JCPOOMusicClient, you do not need to install any additional CLI tools such as ffmpeg or N_m3u8DL-RE. Simply install musicdl via pip and start using it immediately.

#### KKWSMusicClient

KKWSMusicClient now works without requiring extra CLI tools like ffmpeg or N_m3u8DL-RE. After installing musicdl with pip, it is ready to use straight away.

#### LivePOOMusicClient

LivePOOMusicClient operates without reliance on supplementary CLI tools, including ffmpeg and N_m3u8DL-RE. Installation of musicdl via pip alone enables out-of-the-box usage.

#### MituMusicClient

No extra setup. No external CLI tools. Just pip install musicdl and MituMusicClient is ready to use.

#### TwoT58MusicClient

TwoT58MusicClient is designed for hassle-free use: no additional CLI tools like ffmpeg or N_m3u8DL-RE are needed, and a simple pip install musicdl gets everything ready.

#### YinyuedaoMusicClient

You don’t need to install any extra tools like ffmpeg or N_m3u8DL-RE to use YinyuedaoMusicClient — just pip install musicdl and you’re good to go.

#### ZhuolinMusicClient

ZhuolinMusicClient works right out of the box. No ffmpeg, no N_m3u8DL-RE, and no other CLI tools needed — just install musicdl with pip.
