<script>
    import {getRatingColor} from '../utils';
    export let movie;
    const currDate = new Date();
    const currentYear = currDate.getFullYear();
</script>

<style>
    a {
        text-decoration: inherit;
    }

    h6 {
        margin: 0;
    }

    .item-listing-skrn {
        border-radius: 5px;
        border: 1px solid rgba(0,0,0,0.08);
        box-shadow: 0 3px 8px rgba(0,0,0, 0.06);
        width: 100%;
    }

    .item-listing-image-skrn {
        overflow: hidden;
        position: relative;
        max-height: 240px;
    }

    .item-listing-image-skrn:before {
        content: "";
        background: url(../mesh.png) repeat;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        position: absolute;
        z-index: 2;
    }

    .item-listing-skrn img {
        width: 100%;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        cursor: pointer;
        transition: transform .3s, filter .3s ease-in-out;
    }

    .item-listing-skrn:hover img {
        transform: scale(1.2) rotate(5deg);
        filter: brightness(80%);
    }

    .item-listing-text-skrn {
        padding: 0 8px;
        height: 80px;
        width: 100%;
        overflow: hidden;
    }

    .item-listing-year{
        position: absolute;
        top: 4px;
        left: 4px;
        background: #00000070;
        padding: 2px 8px;
        border-radius: 4px;
        font-weight: bold;
        font-size: 20px;
        color: white;
        z-index: 3;
    }

    .item-listing-description {
        display: grid;
        grid-template-columns: 1fr 46px;
        grid-gap: 8px;
        align-items: center;
        height: 80px;
        font-size: 20px;
        line-height: 1.2rem;
    }

    .item-listing-rating-skrn{
        color:#42b740;
        font-weight: 900;
        font-size: 28px;
        line-height: 2em;
    }

    @media (min-width: 768px) {
        .item-listing-text-skrn {
            padding: 0 16px;
        }
        .item-listing-image-skrn {
            max-height: 460px;
        }
    }

    @media (min-width: 1201px) {
        .item-listing-text-skrn {
            padding: 0 24px;
        }
        .item-listing-image-skrn {
            max-height: 424px;
        }
    }

    @media (min-width: 1441px) {
        .item-listing-image-skrn {
            max-height: 370px;
        }
    }

</style>

<a rel='prefetch' href="/movie/{movie.id}">
    <div class="item-listing-skrn">
        <div class="item-listing-image-skrn">
            <div class="item-listing-year"
                 style="color:{movie.year === currentYear ? '#FFEB3B' : 'white'}"
            >
                {movie.year}
            </div>
            <img loading="lazy" width="150" src={movie.poster} alt="Listing">
        </div>
        <div class="item-listing-text-skrn">
            <div class="item-listing-description">
                <h6> {movie.title} </h6>
                <span
                        class="item-listing-rating-skrn"
                        style="color:{getRatingColor(movie.rating)}"
                >
                        {movie.rating}
                </span>
            </div><!-- close .item-listing-text-skrn-vertical-align -->
        </div><!-- close .item-listing-text-skrn -->
    </div>
</a>