# Responsive-video-player
> HTML5 video player


```javascript HTML
<div class="col col-md col-lg">
            <div class="shadow main-video-container ">
                <video src="vid/ex1.mp4" class="main-video" poster="poster/ex1.png" controls preload="auto"></video>
                <h3 class="main-vid-title">Sample video playback</h3>
            </div>
          </div>
          <div class="video-list-container" id="VideosList"></div>
```


```javascript JS
  
const VideosList = [   
    {
        video_src: 'vid/ex1.mp4',
        title:'Example 1 video',
        poster:'poster/ex1.png'
    },
    {
        video_src: 'vid/ex2.mp4',
        title:'Example 2 video',
        poster:'poster/ex2.png'
    },
    {
        video_src: 'vid/ex3.mp4',
        title:'Example 3 video',
        poster:'poster/ex3.png'
    },
    {
        video_src: 'vid/ex4.mp4',
        title:'Example 4 video',
        poster:'poster/ex4.png'
    },
    {
        video_src: 'vid/ex5.mp4',
        title:'Example 5 video',
        poster:'poster/ex5.png'
    }
]

console.log(VideosList);

const catagories = [ ...new Set(VideosList.map((item) => { return item }))];

const videoitemlist = document.getElementById('VideosList');

videoitemlist.innerHTML = catagories.map((item) => {
    //var { video_src, title } = item;   
    var vidsrc = item.video_src;
    var vidtitle = item.title;
    var vidposter = item.poster;
    return (        
        '<div class="list"><video src='+ vidsrc +' class="list-video"  poster='+ vidposter +'></video> <h3 class="list-title">'+ vidtitle +'</h3> </div>'
    )
  
}).join('')

let videoList = document.querySelectorAll('.video-list-container');
videoList.forEach(remove => { remove.classList.remove('active');
//console.log(remove.innerHTML)
})



document.querySelectorAll('.list').forEach(function(item) {
    item.addEventListener('click', function() {    
        console.log(item.innerHTML)  
        let src = item.querySelector('.list-video').src;    
        let postersrc = item.querySelector('.list-video').poster;  
        console.log(src);  
        let title = item.querySelector('.list-title').innerHTML;
        console.log(title);    
        document.querySelector('.main-video-container .main-video').src = src;      
        document.querySelector('.main-video-container .main-video').poster = postersrc;     
        document.querySelector('.main-video-container .main-vid-title').innerHTML = title;        
        document.querySelector('.main-video-container .main-video').play();
    });
    
});


```
