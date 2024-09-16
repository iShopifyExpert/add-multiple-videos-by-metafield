# add-multiple-videos-by-metafield
Add Multiple Videos by Metafields on Product or Collection Page

    {% assign videos = product.metafields.custom.add_products_video.value %}
    {% for video_url in videos %}
      {% assign video_data = "{{ video_url | json }}" %}
      <div class="slick-slide slide">
       <video controls poster="{{ video_data.preview_image.src }}" muted autoplay loop playsinline id="video-{{ video_data.id }}" class="lazy" style="max-width: 100%; height: auto;">
         {% for source in video_data.sources %}
           <source src="{{ source.url | prepend: 'https:' }}" type="{{ source.mime_type }}" media="(min-width: {{ source.width }}px)" size="{{ source.height }}">
         {% endfor %}
         Your browser does not support the video tag.
       </video>
     </div>
    {% endfor %}
