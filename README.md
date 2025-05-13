# Shady-game<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rise of Shady: The Quest for Greatness</title>
  <script src="https://cdn.jsdelivr.net/npm/react@18.2.0/umd/react.production.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/react-dom@18.2.0/umd/react-dom.production.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/babel-standalone@7.22.9/babel.min.js"></script>
  <style>
    /* Pre-built Tailwind CSS (minified, verified for no conflicts) */
    :root {
      --tw-bg-opacity: 1;
      --tw-text-opacity: 1;
      --tw-gradient-from: #1f2937;
      --tw-gradient-to: #111827;
    }
    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background-color: #111827;
      color: #ffffff;
    }
    .min-h-screen { min-height: 100vh; }
    .p-4 { padding: 1rem; }
    .bg-gradient-to-b { background-image: linear-gradient(to bottom, var(--tw-gradient-from), var(--tw-gradient-to)); }
    .from-gray-900 { --tw-gradient-from: #111827; }
    .to-gray-800 { --tw-gradient-to: #1f2937; }
    .text-3xl { font-size: 1.875rem; line-height: 2.25rem; }
    .font-bold { font-weight: 700; }
    .text-center { text-align: center; }
    .mb-4 { margin-bottom: 1rem; }
    .text-yellow-400 { color: #facc15; }
    .text-lg { font-size: 1.125rem; line-height: 1.75rem; }
    .w-64 { width: 16rem; }
    .mx-auto { margin-left: auto; margin-right: auto; }
    .mt-2 { margin-top: 0.5rem; }
    .h-2 { height: 0.5rem; }
    .bg-gray-700 { background-color: #374151; }
    .rounded { border-radius: 0.25rem; }
    .bg-green-500 { background-color: #22c55e; }
    .mb-6 { margin-bottom: 1.5rem; }
    .text-xl { font-size: 1.25rem; line-height: 1.75rem; }
    .font-semibold { font-weight: 600; }
    .text-yellow-300 { color: #fde68a; }
    .grid { display: grid; }
    .grid-cols-1 { grid-template-columns: repeat(1, minmax(0, 1fr)); }
    .sm\:grid-cols-2 { @media (min-width: 640px) { grid-template-columns: repeat(2, minmax(0, 1fr)); } }
    .gap-4 { gap: 1rem; }
    .p-2 { padding: 0.5rem; }
    .bg-gray-600 { background-color: #4b5563; }
    .mb-2 { margin-bottom: 0.5rem; }
    .flex { display: flex; }
    .justify-between { justify-content: space-between; }
    .items-center { align-items: center; }
    .px-3 { padding-left: 0.75rem; padding-right: 0.75rem; }
    .py-1 { padding-top: 0.25rem; padding-bottom: 0.25rem; }
    .bg-yellow-500 { background-color: #eab308; }
    .text-black { color: #000000; }
    .rounded-lg { border-radius: 0.5rem; }
    .hover\:bg-yellow-600:hover { background-color: #ca8a04; }
    .hover\:bg-green-600:hover { background-color: #16a34a; }
    .bg-gray-500 { background-color: #6b7280; }
    .cursor-not-allowed { cursor: not-allowed; }
    .px-6 { padding-left: 1.5rem; padding-right: 1.5rem; }
    .py-2 { padding-top: 0.5rem; padding-bottom: 0.5rem; }
    .bg-blue-500 { background-color: #3b82f6; }
    .hover\:bg-blue-600:hover { background-color: #2563eb; }
    .capitalize { text-transform: capitalize; }
    .error { color: #f87171; font-size: 1.25rem; text-align: center; padding: 2rem; }
  </style>
</head>
<body>
  <div id="root"></div>
  <script type="text/babel" data-presets="react">
    console.log('Loading Rise of Shady app...');
    const { useState, useEffect } = React;

    // Error Boundary Component
    class ErrorBoundary extends React.Component {
      state = { hasError: false, error: null };
      static getDerivedStateFromError(error) {
        return { hasError: true, error };
      }
      render() {
        if (this.state.hasError) {
          return (
            <div className="error">
              <p>Error: {this.state.error?.message || 'Something went wrong'}</p>
              <p>Try refreshing or clearing browser cache.</p>
            </div>
          );
        }
        return this.props.children;
      }
    }

    const initialStats = {
      medical: { xp: 0, level: 1, rank: 'Bronze Healer' },
      russian: { xp: 0, level: 1, rank: 'Bronze Speaker' },
      fitness: { xp: 0, level: 1, rank: 'Bronze Brawler' },
      content: { xp: 0, level: 1, rank: 'Bronze Creator' },
      problem: { xp: 0, level: 1, rank: 'Bronze Handyman' },
      social: { xp: 0, level: 1, rank: 'Bronze Presence' }
    };

    const rewards = [
      { id: 1, name: 'Premium Headphones', cost: 50, type: 'Gear' },
      { id: 2, name: 'Workout Gear', cost: 75, type: 'Gear' },
      { id: 3, name: 'New Outfit', cost: 100, type: 'Gear' },
      { id: 4, name: 'Day Trip', cost: 150, type: 'Freedom' },
      { id: 5, name: 'Custom Phone Setup', cost: 50, type: 'Freedom' },
      { id: 6, name: 'Food Delivery Pass', cost: 75, type: 'Freedom' },
      { id: 7, name: 'Social Media Flex', cost: 50, type: 'Status' },
      { id: 8, name: 'University Rep Boost', cost: 100, type: 'Status' },
      { id: 9, name: 'Personalized Playlist', cost: 25, type: 'Status' },
      { id: 10, name: 'Language Tutor Session', cost: 150, type: 'Tool' }
    ];

    const App = () => {
      const [stats, setStats] = useState(() => {
        try {
          const saved = localStorage.getItem('shadyStats');
          return saved ? JSON.parse(saved) : initialStats;
        } catch (e) {
          console.error('Error loading stats:', e);
          return initialStats;
        }
      });
      const [shadyCoins, setShadyCoins] = useState(() => {
        try {
          const saved = localStorage.getItem('shadyCoins');
          return saved ? parseInt(saved) : 0;
        } catch (e) {
          console.error('Error loading coins:', e);
          return 0;
        }
      });
      const [freedomMeter, setFreedomMeter] = useState(() => {
        try {
          const saved = localStorage.getItem('freedomMeter');
          return saved ? parseInt(saved) : 1;
        } catch (e) {
          console.error('Error loading freedom meter:', e);
          return 1;
        }
      });
      const [purchasedRewards, setPurchasedRewards] = useState(() => {
        try {
          const saved = localStorage.getItem('purchasedRewards');
          return saved ? JSON.parse(saved) : [];
        } catch (e) {
          console.error('Error loading rewards:', e);
          return [];
        }
      });

      useEffect(() => {
        try {
          localStorage.setItem('shadyStats', JSON.stringify(stats));
          localStorage.setItem('shadyCoins', shadyCoins);
          localStorage.setItem('freedomMeter', freedomMeter);
          localStorage.setItem('purchasedRewards', JSON.stringify(purchasedRewards));
          console.log('Progress saved to localStorage');
        } catch (e) {
          console.error('Error saving to localStorage:', e);
        }
      }, [stats, shadyCoins, freedomMeter, purchasedRewards]);

      const updateStat = (stat, xp, sc) => {
        setStats(prev => {
          const newStats = { ...prev };
          newStats[stat].xp += xp;
          newStats[stat].level = Math.floor(newStats[stat].xp / 100) + 1;
          newStats[stat].rank = getRank(newStats[stat].xp);
          return newStats;
        });
        setShadyCoins(prev => prev + sc);
        if (sc > 0) setFreedomMeter(prev => Math.min(prev + 1, 10));
      };

      const buyReward = (reward) => {
        if (shadyCoins >= reward.cost && !purchasedRewards.includes(reward.id)) {
          setShadyCoins(prev => prev - reward.cost);
          setPurchasedRewards(prev => [...prev, reward.id]);
          setFreedomMeter(prev => Math.min(prev + 2, 10));
        }
      };

      const getRank = (xp) => {
        if (xp >= 1501) return 'Grand Champion';
        if (xp >= 1001) return 'Platinum';
        if (xp >= 601) return 'Gold';
        if (xp >= 301) return 'Silver';
        return 'Bronze';
      };

      const saveProgress = () => {
        try {
          localStorage.setItem('shadyStats', JSON.stringify(stats));
          localStorage.setItem('shadyCoins', shadyCoins);
          localStorage.setItem('freedomMeter', freedomMeter);
          localStorage.setItem('purchasedRewards', JSON.stringify(purchasedRewards));
          alert('Progress saved!');
        } catch (e) {
          alert('Error saving progress. Try again.');
          console.error('Save error:', e);
        }
      };

      const quests = {
        daily: [
          { id: 'med1', name: 'Watch 15 min of doctor’s video + 5 UWorld questions', stat: 'medical', xp: 10, sc: 5 },
          { id: 'rus1', name: 'Watch 10 min Russian reels, repeat 3 phrases', stat: 'russian', xp: 10, sc: 5 },
          { id: 'fit1', name: '15 min bodyweight workout', stat: 'fitness', xp: 10, sc: 5 },
          { id: 'soc1', name: 'Journal 1 growth sentence', stat: 'social', xp: 5, sc: 5 },
          { id: 'con1', name: 'Study 1 trending TikTok', stat: 'content', xp: 5, sc: 5 },
          { id: 'pro1', name: 'Watch 5 min skill video (e.g., cooking)', stat: 'problem', xp: 5, sc: 5 }
        ],
        weekly: [
          { id: 'med2', name: 'Review 1 course topic, summarize in 3 sentences', stat: 'medical', xp: 20, sc: 15 },
          { id: 'rus2', name: 'Learn 10 Russian words, use 5 in sentences', stat: 'russian', xp: 20, sc: 15 },
          { id: 'fit2', name: 'Eat 1 high-protein meal/day for 5 days', stat: 'fitness', xp: 20, sc: 15 },
          { id: 'soc2', name: 'Do 1 social action (e.g., compliment someone)', stat: 'social', xp: 20, sc: 15 },
          { id: 'con2', name: 'Post 1 TikTok video', stat: 'content', xp: 20, sc: 15 },
          { id: 'pro2', name: 'Help 1 person with a small task', stat: 'problem', xp: 20, sc: 15 }
        ],
        monthly: [
          { id: 'med3', name: '20 UWorld questions/day, 5 days/week for 2 weeks', stat: 'medical', xp: 50, sc: 50 },
          { id: 'rus3', name: 'Chat 30 min with language partner or say hi to 2 locals', stat: 'russian', xp: 50, sc: 50 },
          { id: 'fit3', name: '4 workouts/week for 4 weeks, take progress photo', stat: 'fitness', xp: 50, sc: 50 },
          { id: 'soc3', name: 'Share 1 win publicly (e.g., TikTok)', stat: 'social', xp: 50, sc: 50 },
          { id: 'con3', name: 'Learn 1 editing skill, use in TikTok', stat: 'content', xp: 50, sc: 50 },
          { id: 'pro3', name: 'Learn 1 skill (e.g., cook meal) and use it', stat: 'problem', xp: 50, sc: 50 }
        ],
        boss: [
          { id: 'boss1', name: 'USMLE Gatekeeper: Make USMLE study plan', stat: 'medical', xp: 100, sc: 100 },
          { id: 'boss2', name: 'Social Icebreaker: 5 min Russian convo', stat: 'russian', xp: 100, sc: 100 },
          { id: 'boss3', name: 'Strength Berserker: 50 push-ups or 5km run', stat: 'fitness', xp: 100, sc: 100 },
          { id: 'boss4', name: 'Viral Challenger: TikTok with 500+ views', stat: 'content', xp: 100, sc: 100 },
          { id: 'boss5', name: 'Solution Master: Solve complex problem', stat: 'problem', xp: 100, sc: 100 },
          { id: 'boss6', name: 'Respect Earner: Get feedback from 2 people', stat: 'social', xp: 100, sc: 100 }
        ]
      };

      return (
        <div className="min-h-screen p-4 bg-gradient-to-b from-gray-900 to-gray-800">
          <h1 className="text-3xl font-bold text-center mb-4 text-yellow-400">Rise of Shady: The Quest for Greatness</h1>
          <div className="text-center mb-4">
            <p className="text-lg">Level: {Math.floor(Object.values(stats).reduce((sum, s) => sum + s.xp, 0) / 1000) + 1} | Shady Coins: {shadyCoins}</p>
            <div className="w-64 mx-auto mt-2">
              <p>Freedom Meter: {freedomMeter}/10</p>
              <div className="h-2 bg-gray-700 rounded">
                <div className="h-2 bg-green-500 rounded" style={{ width: `${freedomMeter * 10}%` }}></div>
              </div>
            </div>
          </div>

          <div className="mb-6">
            <h2 className="text-xl font-semibold mb-2 text-yellow-300">Stat Tracker</h2>
            <div className="grid grid-cols-1 sm:grid-cols-2 gap-4">
              {Object.entries(stats).map(([key, stat]) => (
                <div key={key} className="p-4 bg-gray-700 rounded-lg">
                  <p className="font-bold">{key === 'medical' ? 'Medical Mastery' : key === 'russian' ? 'Russian Edge' : key === 'fitness' ? 'Physical Power' : key === 'content' ? 'Content Hustle' : key === 'problem' ? 'Problem-Solving Prowess' : 'Social Swagger'}</p>
                  <p>XP: {stat.xp} | Level: {stat.level}</p>
                  <p>Rank: {stat.rank}</p>
                </div>
              ))}
            </div>
          </div>

          <div className="mb-6">
            <h2 className="text-xl font-semibold mb-2 text-yellow-300">Quest Log</h2>
            {['daily', 'weekly', 'monthly', 'boss'].map(type => (
              <div key={type} className="mb-4">
                <h3 className="text-lg font-medium capitalize">{type} Quests</h3>
                {quests[type].map(quest => (
                  <div key={quest.id} className="p-2 bg-gray-600 rounded-lg mb-2 flex justify-between items-center">
                    <p>{quest.name}</p>
                    <button
                      onClick={() => updateStat(quest.stat, quest.xp, quest.sc)}
                      className="px-3 py-1 bg-yellow-500 text-black rounded hover:bg-yellow-600"
                    >
                      Complete
                    </button>
                  </div>
                ))}
              </div>
            ))}
          </div>

          <div className="mb-6">
            <h2 className="text-xl font-semibold mb-2 text-yellow-300">Reward Shop</h2>
            <div className="grid grid-cols-1 sm:grid-cols-2 gap-4">
              {rewards.map(reward => (
                <div key={reward.id} className="p-4 bg-gray-700 rounded-lg flex justify-between items-center">
                  <div>
                    <p className="font-bold">{reward.name}</p>
                    <p>Cost: {reward.cost} SC | Type: {reward.type}</p>
                  </div>
                  <button
                    onClick={() => buyReward(reward)}
                    disabled={shadyCoins < reward.cost || purchasedRewards.includes(reward.id)}
                    className={`px-3 py-1 rounded ${shadyCoins < reward.cost || purchasedRewards.includes(reward.id) ? 'bg-gray-500 cursor-not-allowed' : 'bg-green-500 hover:bg-green-600'}`}
                  >
                    {purchasedRewards.includes(reward.id) ? 'Owned' : 'Buy'}
                  </button>
                </div>
              ))}
            </div>
          </div>

          <div className="text-center">
            <button
              onClick={saveProgress}
              className="px-6 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
            >
              Save Progress
            </button>
          </div>
        </div>
      );
    };

    // Use createRoot for React 18
    console.log('Rendering app...');
    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(
      <ErrorBoundary>
        <App />
      </ErrorBoundary>
    );
    console.log('App rendered');
  </script>
</body>
</html>
