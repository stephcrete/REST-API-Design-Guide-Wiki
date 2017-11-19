<table>
  <tbody>
    <tr>
      <th align="center">Version</th>
      <th align="center">Date</th>
      <th align="center">Author</th>
      <th align="left">Comments</th>
    </tr>
    <tr>
      <td align="center">1.6</td>
      <td align="center">2017-11-18</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Bulk operations: added details about concurrency and how to pass the ETags in the update requests</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.5</td>
      <td align="center">2017-06-15</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Pagination: changed the name of the exclude metadata query parameter to "excludeMetadata"</li>
          <li>Pagination: added some naming conventions for query parameters (should be camelCase)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.4</td>
      <td align="center">2017-05-22</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Error handling: added the possibility to provide metadata in error payloads: [[Error handling Error details]]. Example: [[Error handling Example with additional metadata]]</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.3</td>
      <td align="center">2017-05-17</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Error handling: added a page for providing some guidance regarding how to handle "warnings": [[Error handling Warnings]]</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.2</td>
      <td align="center">2016-12-15</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Concurrency: explained that HTTP 428 (Precondition Failed) should be returned by the server if it expected a conditional request and it wasn't</li>
          <li>Explained usage of 429 (Too Many Requests)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.1</td>
      <td align="center">2016-12-14</td>
      <td align="center">@dSebastien</td>
      <td align="left">
          <ul>
            <li>Clarified that our design guide is not fully RESTful (no HATEOAS)</li>
          </ul>
      </td>
    </tr>
    <tr>
      <td align="center">1.0</td>
      <td align="center">2016-12-09</td>
      <td align="center">@dSebastien</td>
      <td align="left">
        <ul>
          <li>Published on GitHub</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>