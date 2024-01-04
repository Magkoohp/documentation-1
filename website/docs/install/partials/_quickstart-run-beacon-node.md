import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<p className='hidden-in-jwt-guide hidden-in-mergeprep-guide'>In this step, you'll run a beacon node using Prysm.</p>
<p>There is two main ways to sync a beacon node: from genesis, and from a checkpoint. It is safer and a considerably faster to sync from a checkpoint. When syncing from a checkpoint, the simplest is to connect to a checkpoint sync endpoint. A non exhaustive <a href='https://eth-clients.github.io/checkpoint-sync-endpoints'> list of checkpoint sync endpoints</a> is available.</p>
<p>In the following examples, we'll use the checkpoint sync endpoint provided by <a href='https://beaconstate.info/'>beaconstate.info</a>. <strong>Feel free to use the one you want.</strong></p>
<Tabs groupId="os" defaultValue="others" values={[
    {label: 'Windows', value: 'win'},
    {label: 'Linux, MacOS, Arm64', value: 'others'}
]}>
  <TabItem value="win">
    <Tabs groupId="network" defaultValue="mainnet" values={[
      {label: 'Mainnet', value: 'mainnet'},
      {label: 'Goerli', value: 'goerli'},
      {label: 'Sepolia', value: 'sepolia'},
      {label: 'Holesky', value: 'holesky'}
    ]}>
      <TabItem value="mainnet">
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt">
            <p>Navigate to your <code>consensus</code> directory and run the following command to start your beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_JWT_FILE&gt;</code> by the path to the JWT file generated during the previous step:</p>
            <pre><code>prysm.bat beacon-chain --execution-endpoint=http://localhost:8551 --mainnet --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --checkpoint-sync-url=https://beaconstate.info --genesis-beacon-api-url=https://beaconstate.info</code></pre>
          </TabItem>
          <TabItem value="ipc">
            <p>Navigate to your <code>consensus</code> directory and run the following command to start your beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
            <pre><code>prysm.bat beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --mainnet --checkpoint-sync-url=https://beaconstate.info --genesis-beacon-api-url=https://beaconstate.info</code></pre>
          </TabItem>
        </Tabs>
      </TabItem>
      <TabItem value="goerli">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/eth2-networks/raw/master/shared/prater/genesis.ssz'>Goerli genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt"><pre><code>prysm.bat beacon-chain --execution-endpoint=http://localhost:8551 --goerli --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://goerli.beaconstate.info --genesis-beacon-api-url=https://goerli.beaconstate.info</code></pre></TabItem>
          <TabItem value="ipc"><pre><code>prysm.bat beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --goerli --genesis-state=genesis.ssz --checkpoint-sync-url=https://goerli.beaconstate.ethstaker.cc --genesis-beacon-api-url=https://goerli.beaconstate.ethstaker.cc</code></pre></TabItem>
        </Tabs>
        <p>You may wonder why the previous link contains the "Prater" word instead of "Goerli". The reason is, in the pre-merge world, "Goerli" was the name of the execution layer for this testnet, and "Prater" the name of the consensus layer for this testnet. Post-merge, the name "Prater" was deprecated and now only "Goerli" remains.</p>
      </TabItem>
      <TabItem value="sepolia">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/merge-testnets/blob/main/sepolia/genesis.ssz'>Sepolia genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt"><pre><code>prysm.bat beacon-chain --execution-endpoint=http://localhost:8551 --sepolia --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://sepolia.beaconstate.info --genesis-beacon-api-url=https://sepolia.beaconstate.info</code></pre></TabItem>
          <TabItem value="ipc"><pre><code>prysm.bat beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --sepolia --genesis-state=genesis.ssz --checkpoint-sync-url=https://sepolia.beaconstate.info --genesis-beacon-api-url=https://sepolia.beaconstate.info</code></pre></TabItem>
        </Tabs>
      </TabItem>
      <TabItem value="holesky">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/holesky/blob/main/custom_config_data/genesis.ssz'>Holesky genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt"><pre><code>prysm.bat beacon-chain --execution-endpoint=http://localhost:8551 --holesky --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://holesky.beaconstate.info --genesis-beacon-api-url=https://holesky.beaconstate.info</code></pre></TabItem>
          <TabItem value="ipc"><pre><code>prysm.bat beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --holesky --genesis-state=genesis.ssz --checkpoint-sync-url=https://holesky.beaconstate.info --genesis-beacon-api-url=https://holesky.beaconstate.info</code></pre></TabItem>
        </Tabs>
      </TabItem>
    </Tabs>
  </TabItem>
  <TabItem value="others">
    <Tabs groupId="network" defaultValue="mainnet" values={[
      {label: 'Mainnet', value: 'mainnet'},
      {label: 'Goerli', value: 'goerli'},
      {label: 'Sepolia', value: 'sepolia'},
      {label: 'Holesky', value: 'holesky'}
    ]}>
      <TabItem value="mainnet">
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt">
            <p>Navigate to your <code>consensus</code> directory and run the following command to start your beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_JWT_FILE&gt;</code> by the path to the JWT file generated during the previous step:</p>
            <pre><code>./prysm.sh beacon-chain --execution-endpoint=http://localhost:8551 --mainnet --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --checkpoint-sync-url=https://beaconstate.info --genesis-beacon-api-url=https://beaconstate.info</code></pre>
          </TabItem>
          <TabItem value="ipc">
            <p>Navigate to your <code>consensus</code> directory and run the following command to start your beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
            <pre><code>./prysm.sh beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --mainnet --checkpoint-sync-url=https://beaconstate.info --genesis-beacon-api-url=https://beaconstate.info</code></pre>
          </TabItem>
        </Tabs>
      </TabItem>
      <TabItem value="goerli">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/eth2-networks/raw/master/shared/prater/genesis.ssz'>Goerli genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
          ]}>
            <TabItem value="jwt"><pre><code>./prysm.sh beacon-chain --execution-endpoint=http://localhost:8551 --goerli --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://goerli.beaconstate.info --genesis-beacon-api-url=https://goerli.beaconstate.info</code></pre></TabItem>
            <TabItem value="ipc"><pre><code>./prysm.sh beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --goerli --genesis-state=genesis.ssz --checkpoint-sync-url=https://goerli.beaconstate.info --genesis-beacon-api-url=https://goerli.beaconstate.info</code></pre></TabItem>
          </Tabs>
          <p>You may wonder why the previous link contains the "Prater" word instead of "Goerli". The reason is, in the pre-merge world, "Goerli" was the name of the execution layer for this testnet, and "Prater" the name of the consensus layer for this testnet. Post-merge, the name "Prater" was deprecated and now only "Goerli" remains.</p>
      </TabItem>
      <TabItem value="sepolia">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/merge-testnets/blob/main/sepolia/genesis.ssz'>Sepolia genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt"><pre><code>./prysm.sh beacon-chain --execution-endpoint=http://localhost:8551 --sepolia --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://sepolia.beaconstate.info --genesis-beacon-api-url=https://sepolia.beaconstate.info</code></pre></TabItem>
          <TabItem value="ipc"><pre><code>./prysm.sh beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --sepolia --genesis-state=genesis.ssz --checkpoint-sync-url=https://sepolia.beaconstate.info --genesis-beacon-api-url=https://sepolia.beaconstate.info</code></pre></TabItem>
          </Tabs>
      </TabItem>
      <TabItem value="holesky">
        <p className='hidden-in-jwt-guide'>Download the <a href='https://github.com/eth-clients/holesky/blob/main/custom_config_data/genesis.ssz'>Holesky genesis state from Github</a> into your <code>consensus</code> directory. Then use the following command to start a beacon node that connects to your local execution node by replacing <code>&lt;PATH_TO_IPC_FILE&gt;</code> by the path to the IPC file the execution client created for you during the previous step:</p>
        <Tabs groupId="protocol" defaultValue="jwt" values={[
          {label: 'JWT', value: 'jwt'},
          {label: 'IPC', value: 'ipc'}
        ]}>
          <TabItem value="jwt"><pre><code>./prysm.sh beacon-chain --execution-endpoint=http://localhost:8551 --holesky --jwt-secret=&lt;PATH_TO_JWT_FILE&gt; --genesis-state=genesis.ssz --checkpoint-sync-url=https://holesky.beaconstate.info --genesis-beacon-api-url=https://holesky.beaconstate.info</code></pre></TabItem>
          <TabItem value="ipc"><pre><code>./prysm.sh beacon-chain --execution-endpoint=&lt;PATH_TO_IPC_FILE&gt; --holesky --genesis-state=genesis.ssz --checkpoint-sync-url=https://holesky.beaconstate.info --genesis-beacon-api-url=https://holesky.beaconstate.info</code></pre></TabItem>
        </Tabs>
      </TabItem>
    </Tabs>
  </TabItem>
</Tabs>

<div className='hidden-in-jwt-guide hidden-in-mergeprep-guide'>

Syncing from a checkpoint usually takes a couple of minutes. See [Sync from a checkpoint](../../prysm-usage/checkpoint-sync.md) for more information about this feature.

If you wish to sync from genesis, you need to remove <code>--checkpoint-sync-url</code> and <code>--genesis-beacon-api-url</code> flags from the previous command. Syncing from genesis usually takes a couple days, but it can take longer depending on your network and hardware specs.

If you are planning to run a validator, it is <strong>strongly</strong> advised to use the <code>--suggested-fee-recipient=<WALLET ADDRESS\></code> option. When your validator proposes a block, it will allow you to earn block priority fees, also sometimes called "tips".


<p className="hidden-in-mergeprep-guide">Congratulations - you’re now running a <strong>full Ethereum node</strong>. To check the status of your node, visit <a href='https://docs.prylabs.network/docs/monitoring/checking-status'>Check node and validator status</a>.</p>

</div>
