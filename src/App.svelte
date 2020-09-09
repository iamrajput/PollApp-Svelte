<script>
import Header from './components/Header.svelte';
import Footer from './components/Footer.svelte';
import CreatePollForm from './components/CreatePollForm.svelte';
import PollList from './components/PollList.svelte';
import Tabs from './shared/Tabs.svelte';
//tabs
let items = ['Current Polls', 'Add new polls'];
let activeItem = 'Current Polls';
const tabchange = (e) => {
  activeItem = e.detail;
}

const handleAddPoll = (e) => {
  // const poll = e.detail
  // polls = [poll,...polls]
  // console.log(polls);
  activeItem = 'Current Polls'

}

// const handleVoteUpdate = (e) => {
//       const {id,option} = e.detail
//       let copiedPolls = [...polls]
//       let upvotedPoll = copiedPolls.find((poll) => poll.id == id);
//       if(option === 'a'){
//         upvotedPoll.votesA++;
//       }
//       if(option === 'b'){
//         upvotedPoll.votesB++;
//       }

//       polls = copiedPolls;
      
// }




</script>
<Header />
<main>
   <Tabs {activeItem} {items} on:tabchange={tabchange}/>
   {#if activeItem === 'Current Polls'}
  <PollList />
   {:else if activeItem ==='Add new polls'}
   <CreatePollForm on:add_poll={handleAddPoll}/>
   {/if}
</main>
<Footer />

<style>
	main{
    width: 100%;
    max-width: 960px;
    margin: 40px auto;
  }
</style>