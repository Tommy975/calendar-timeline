<script>
    import {getContext} from 'svelte';
    import {setContent, toISOString, toSeconds, addDay} from '@event-calendar/core';
    let {_headerEl, _intlDayHeader, _intlDayHeaderAL, _dayTimes, _viewDates, _viewMonths, slotDuration, theme} = getContext('state');
</script>

{#if toSeconds($slotDuration)}

    <!-- <div class="{$theme.header}" bind:this={$_headerEl}>
        <div class="{$theme.days}" role="row">
            {#each $_viewDates as date} -->
    <div class="{$theme.header}" bind:this={$_headerEl}>
        <div class="ec-months"  role="row">
            {#each Object.entries($_viewMonths) as [key, month]}
                <div class="ec-month ">
                    <span class="span-month">{key}</span>
                    <div class="{$theme.days}" role="row">

                        {#each month as date}
                            <div class="{$theme.day} {$theme.weekdays?.[date.getUTCDay()]}">
                                <div class="{$theme.dayHead}">
                                    <time
                                        datetime="{toISOString(date, 10)}"
                                        aria-label="{$_intlDayHeaderAL.format(date)}"
                                        use:setContent={$_intlDayHeader.format(date)}
                                    ></time>
                                </div>
                                <div class="{$theme.times}">
                                    {#each $_dayTimes[date.getTime()] as time}
                                        <div class="{$theme.time}" role="columnheader">
                                            <time
                                                datetime="{time[0]}"
                                                use:setContent={time[1]}
                                            ></time>
                                        </div>
                                    {/each}
                                </div>
                            </div>   
                        {/each} 
                    </div>
                </div>
                {/each}
            </div>
        <div class="{$theme.hiddenScroll}"></div>
    </div>
{:else}
    <div class="{$theme.header}" bind:this={$_headerEl}>
        <div class="ec-months"  role="row">
            {#each Object.entries($_viewMonths) as [key, month]}
                <div class="ec-month ">
                    <span class="span-month">{key}</span>
                    <div class="{$theme.days}" role="row">

                        {#each month as date}

                            <div class="{$theme.day} {$theme.weekdays?.[date.getUTCDay()]}">
                                <div class="{$theme.time}" role="columnheader">
                                    <time
                                        datetime="{toISOString(date, 10)}"
                                        aria-label="{$_intlDayHeaderAL.format(date)}"
                                        use:setContent={$_intlDayHeader.format(date)}
                                    ></time>
                                </div>
                            </div>
                        {/each}
                    </div>
                </div>
            {/each}
        </div>
    </div>
{/if}
 