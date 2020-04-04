This is my repositary

Introduction to HTML, CSS to create a basic portfolio-website

Google

git status

git commit -m "file.md"

git add file.md

git add -A

git add -li

git commit -m "mesage"

git push origin master

git config --global user.name "Maheshababubugide"

aws s3 cp . s3://tap.ibhubs.in/2019/maheshbabu-bugide --recursive --exclude ".c9/*"

rm filename

wget absolute-url

def get_movies_by_given_cast_objects(cast_objs):
    if len(cast_objs):
        movie_lst = []
        movie_list=[]
        cast_list = []
        movie_dict = {}
        flag1 = 0
        for cast in cast_objs:
            cast_dict = {}
            if cast.movie not in movie_lst:
                if True:
                    if flag1: 
                        movie_dict['cast'] = cast_list
                        movie_list.append(movie_dict)
                    flag1 = 1
                    cast_list = []
                movie_lst.append(cast.movie)
                movie_obj = cast.movie
                movie_dict = {}
                movie_dict['movie_id'] = movie_obj.movie_id
                movie_dict['name'] = movie_obj.name
                movie_dict['box_office_collection_in_crores'] = movie_obj.box_office_collection_in_crores
                movie_dict['release_date'] = str(movie_obj.release_date)
                movie_dict['director_name'] = movie_obj.director.name
                movie_dict['average_rating'] = get_average_rating_of_movie(movie_obj)
                movie_dict['total_number_of_ratings'] = total_number_of_ratings(movie_obj)
            actor_dict = {}
            actor_dict['name'] = cast.actor.name
            actor_dict['actor_id'] = cast.actor_id
            cast_dict['actor'] = actor_dict
            cast_dict['role'] = cast.role
            cast_dict['is_debut_movie'] = cast.is_debut_movie
            cast_list.append(cast_dict)
        movie_dict['cast'] = cast_list
        movie_list.append(movie_dict) 
        return movie_list
    else:
        return []
        
 female_count = Count('actors',distinct = True,filter = Q(actors__gender='FEMALE'))
    cast_objs = Cast.objects.filter(movie__in=Movie.objects.annotate(
        female_count = female_count).filter(
            female_count__gt=5)).filter(actor__gender='FEMALE').select_related(
                        'movie__director','movie__rating','actor'
                        )
    return get_movies_by_given_cast_objects(cast_objs)
 
 
 def get_actor_movies_released_in_year_greater_than_or_equal_to_2000():
    
    queryset = Movie.objects.filter(release_date__year__gte=2000).select_related('director','rating').prefetch_related('cast_set')
    actor_objs = Actor.objects.filter(movie__release_date__year__gte=2000).prefetch_related(
            Prefetch('movie_set',queryset = queryset,to_attr = 'movies')
            )
    actors_list = []
    for actor in actor_objs:
        actor_dict = {}
        actor_dict['name'] = actor.name
        actor_dict['actor_id'] = actor.actor_id
        movies_list = []
        for movie in actor.movies:
            movie_dict = {}
            movie_dict['movie_id'] = movie.movie_id
            movie_dict['name'] = movie.name
            casts_list = []
            for cast in movie.cast_set.all():
                cast_dict = {}
                if cast.actor_id == actor.actor_id:
                    cast_dict['role'] = cast.role
                    cast_dict['is_debut_movie'] = cast.is_debut_movie
                    casts_list.append(cast_dict)
            movie_dict['cast'] = casts_list
            movie_dict['box_office_collection_in_crores'] = movie.box_office_collection_in_crores
            movie_dict['release_date'] = str(movie.release_date)
            movie_dict['director_name'] = movie.director.name
            movie_dict['average_rating'] = get_average_rating_of_movie(movie)
            movie_dict['total_number_of_ratings'] = total_number_of_ratings(movie)
            movies_list.append(movie_dict)
        actor_dict['movies'] = movies_list
        actors_list.append(actor_dict)
    return actors_list


        
        <meta charset="utf-8">
        <meta http.equiv="X-UA-Compatible" content="IE-edge">
        <meta name="viewport" content="width=device-width, initial-scale=1,
        shrink-to-fit=no">
        <link rel="stylesheet" href="bootstrap/bootstrap.min.css">
        <script src="bootstrap/jquery.min.js"></script>
        <script src="bootstrap/popper.min.js"></script>
        <script src="bootstrap/bootstrap.min.js"></script>
        <script src="https://tap.ibhubs.in/utils/flex-item-width.js"></script>
        
        extra small devices(class_prefix : col- ) < 576px(device_size width)
        small devices (class_prefix : col-sm- ) >= 576px
        medium devices (class_prefix : col-md- ) >= 768px
        large devices (class_prefix : col-lg- ) >= 992px
        extra large devices (class_prefix : col-xl- ) >= 1200px
        
        

        https://hackerthemes.com/bootstrap-cheatsheet/
        
        portfolio-website/assignment-12/assignment_12_v2.html
        
        portfolio-website/assignment-13/13dup.html
        
        
        https://hackerthemes.com/bootstrap-cheatsheet/#card-subtitle

https://icons.getbootstrap.com

https://fontawesome.com/icons?d=gallery&q=fac

https://developer.mozilla.org/en-US/docs/Web/CSS/transform

https://caniuse.com

https://bennettfeely.com/clippy/


flex:initial; 0 1 1;
flex:none; 0 0 0;
flex:auto; 1 1 auto;
flex:1; 1 1 0;
